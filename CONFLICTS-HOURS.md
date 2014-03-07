Hours of Operation and Conflicts
================================
In addition to ensuring that an item does not have a time conflict with another
reservation, reservations will have hours to be bound by. The simplest
system will assume that reservations can occur at any time on any
date, essentially making the hours of operation for that item 24 hours per day
7 days a week.

Since the system should be implemented using an interface, to add hours of
operation one would implement the interface with a more complex conflict
checker and conflict resolver.

While hours of operation could be 7 days a week 9am to 5pm, the general usecase
will most likely require not only hours, but also specific days, and for some
days to be classified as 'weekends'. There should also be a provision to check
if a reservation extends overnight and if overnight reservations are allowed.

There might be two sets of hours of operations: One for the entity
as a whole, the company, and one for the individual reserveable items, such
as a conference room or a camera. The conflict resolution system should be able
to handle this occurrence as well. Since ideally one is a special case of many,
the system should be able to handle an arbitrary number of defined hours of
operation.
