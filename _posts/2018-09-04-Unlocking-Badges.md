---
title: "Unlocking Badges"
date: 2018-09-04
layout: default
---

#2 Event Fakery
Events are good when something triggers multiple actions.
Jeff fakes the events:
```
Event::fake();

Event::assertDispatched(UserEarnedExperience::class);

```
Can also fire events like this (as long as the event has the Dispatchable trait.  ):
```
UserCreated::dispatch;
```

Instead of just checking that the event is dispatched, we can also check the data:

```
Event::assertDispatched(UserRaenedExperience::Class, function ($event){
    return $event->points = 100;
});

```

#3 Use TDD to Construct Migrations and Attributes

TDD to write migrations.

#4 A User Can Be Awarded Achievements

#5

#6

