reserve
=======

> Reserving things is difficult.

Every system out there appears to be specialized
to reserve certain types of things, like hotel rooms, lab equipment, meeting
spaces, or resources. Many of these systems have awesome features, but they're
specific to the system. Equipment reservation systems have lab hours, but
sometimes you want to have studios that are more like hotel rooms than a camera.
Systems that add that functionality cost substantially more than systems which
don't have that hotel like interface.

Even though these expensive systems handle the extra requirements, many of them
are clunky and an eyesore to look at. The cheaper ones can be just as much of an
eyesore. Additionally, these systems require special hardware or OS
requirements, many of them that I've found only run on windows. This adds costs,
 makes it harder for smaller organizations to get started, and adds other costs
like licensing. It's time for some change. It's time to build something we can
throw on any hardware and scale it up later when we need to. We need a platform
that we can use to reserve things. Not to reserve hotel rooms or lab equipment,
just things.

We should be able to plug this system into other systems that exist out there,
like Wordpress, Drupal, Joomla, Symfony, and eventually Rails, Django, .NET and other non
PHP systems.

We need a new way to reserve things, so let's build it.

How do we do it?
----------------
Small steps. Pluggable storage, a RESTFUL API, and the other requirements come
after the first step. It needs to reserve stuff. Reserving stuff doesn't simply
mean I say "I want to reserve Camera A from 10:00pm to 1:00am" that a
reservation is made and everything is good. In the least we have to check to
ensure the reservation we request does not interfere with another reservation.
The reservation overlap can be broken down into 3 different types:

- Reservation A's start time is __after__ Reservation B's start time, but
  __before__ Reservation B's end time.
- Reservation A's start time is __before__ Reservation B's start time, and
  Reservation A's end time is __after__ Reservation A's start time.
- Reservation A's start time is __after__ Reservation B's start time, and
  Reservation A's end time is __before__ Reservation B's end time

