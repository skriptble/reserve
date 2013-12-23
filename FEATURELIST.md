reserve api Feature List
========================

This document will serve as a place for features that can eventually be added to
the reserve api.

1. Suggestion engine for showing possible reservation adjustments if the
reservation requested has a conflict. This feature would only be useful in
certain subsets of the reserve api.
Examples:

  - I request a reservation for camera A from 12:00pm to 4:00pm, but it's
    already reserved until 1:00pm. Suggested reservations could be to use
    camera B instead of to shift the reservation to 1:00pm to 4:00pm.
  - I requested a suite in a hotel, but it's already booked for the week I've
    selected, so another suite is suggested. Amenity and overall price
    comparisons are displayed to give the user additional information.

2. Related item engine that returns items that are often reserved in budles or at
the same time, such as a camera, tripod, and lights or a camera and lab editing
time.
