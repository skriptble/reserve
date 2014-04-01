reserve api
===========

> Reserving things should be simple.

Reservation systems appear to be specialized
to reserve certain types of things, like hotel rooms, lab equipment, meeting
spaces, or resources. Many of these systems have awesome features, but they're
specific to the system. Equipment reservation systems have lab hours, but
sometimes you want to have studios that are more like hotel rooms than a camera.
Systems that add that functionality cost substantially more than systems which
don't have that hotel like interface.

Even though these expensive systems handle the extra requirements, many of them
are clunky and an eyesore to look at. The cheaper ones can be just as much of an
eyesore and they lack features. Additionally, these systems require special hardware or OS
requirements, many of them that I've found only run on windows. This adds costs,
makes it harder for smaller organizations to get started, and adds other costs
like licensing. It's time for some change. It's time to build something we can
throw on any hardware and scale it up later when we need to. We need a platform
that we can use to reserve things. Not to reserve hotel rooms or lab equipment,
just things.

We should be able to plug this system into other systems that exist out there,
like Wordpress, Drupal, Joomla, Symfony, and eventually Rails, Django, .NET and other non
PHP systems. An eventual goal of this project would to make a pure C
implementation of the reserve API, which enables its usage with any language
that supports C bindings (similar to [libgit2](http://libgit2.github.com/) or
[linux containers](https://github.com/lxc/lxc).

We need a new way to reserve things, so let's build it.

How do we do it?
----------------
Small steps. Pluggable storage, a RESTFUL API, and the other requirements come
after the first step. It needs to reserve stuff. Reserving stuff doesn't simply
mean I say "I want to reserve Camera A from 10:00pm to 1:00am" that a
reservation is made and everything is good. In the least we have to check to
ensure the reservation we request does not interfere with another reservation.

First let's evaluate when a reservation will not interfere with the reservation
we are attempting to make. There are two scenarios:

- Reservation A's start time is after Reservation B's end time
- Reservation A's end time is before Reservation B's start time

Since the only known reservation is the one we're making (Reservation A), we
need the second case. To get all the overlaps we flip that non-conflict
scenarios on their head:

- Reservation A's start time is before Reservation B's end time
- Reservation A's end time is after Reservation B's start time

This does not assure an overlap though. Using the example reservation we had
above, if I create a reservation from 2:00am to 3:00am, then Reservation A's
start time is before Reservation B's end time, but there is no overlap.
Therefore, the overlap scenario is an AND of the two, not an OR.

A query would look like the following:

```SQL
SELECT * FROM reservations WHERE reservation.end > {10:00pm} AND
reservation.start < {1:00am}
```
This query would return all the results that result in a conflict. If no results
are returned, there aren't any conflicts. Since the entire result set is being
returned, one could even show an end user the times that are booked.
