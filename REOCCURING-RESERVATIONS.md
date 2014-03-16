Reoccurring & Repeatable Reservations
=====================================
> Reservations should be easily repeatable.

This should be plugged into the conflict workflow and repeating reservations
should be stored in as compact a way as possible. They should have rules and
exceptions dates, when exceptions occur a standalone reservation can be created
that is still part of the repeating set of reservations. This also means that
it would be possible, although not compact, to have repeating reservations as
regular reservations with a searchable identifier that allows them to be updated
as a set.

For systems that wish to keep the reservations types down to one, the
aforementioned system of repeatable reservations simply being regular
reservations with an additional identifier would allow the system data to be
read by an application client that doesn't understand the specifics of a
reoccurring reservation. This type of system would also make it easier to bulk
export reservations as an additional set of functionality to convert the compact
reoccurring reservation into a series of regular reservations would not be
necessary. Ultimately, this method is more semitic than the first as it keeps
the system simpler and makes the recurrence an extension of the reservation
system instead of an independently operating piece.
