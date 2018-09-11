---
title: "Testing Events"
date: 2018-09-04
layout: default
---

# Adam Wathan - Three Approaches To Testing

## How to test for NewFollower Event
```
Event::fire(new NewFollower (Auth::user->id, $userToFollow->id))
```

### 1 Expect Events

```
$this->expectsEvents(NewFollower::class)
```

Test only passes, if event fires.

#### Problem
Parameters could be wrong and test would still pass.

### 2 Could use a traditional mock solution.

```
Event::shouldReceive('fire')->with(new NewFollower($follower->id, $followed->id))->once();
```

This will fail because we are creating a new NewFollower in the test, so it will have a different object id, than the one in the event.

Should be like this:
```
Event::shouldReceive('fire')->with(Mockery::on(function ($event) use ($follower, $followed) {
      return $event->followerId == $follower->id
      && $event->followedId == $followed->id;

})->once();

Event::shouldIgnoreMissing();
```

Adam does not like this because it does not follow:
```// Arrange
// Act
// Assert
```

### 3 Adam Prefers - use a spy instead of a mock

```
public function test_a_user_can_follow_another_user
{
      //Arrange
      Event::spy();
      $follower = factory(User::class)->create(['username' => 'steve']);
      $followed = factory(User::class)->create([
            'username' => 'jane',
            'email' => 'jane@example.com'
       ]);
            
       
       
       //Act
       $this->actingAs($follower)
            ->post('following',['username' => 'jane']);
            
       //Assert
       $this->assertTrue($follower->follows($followed));
       Event::shouldReceive('fire')->with(Mockery::on(function ($event) use ($follower, $followed) {
            return $event->followerId == $follower->id
            && $event->followedId == $followed->id;
        })->once();
       

}

```
Controller:
```
Event::fire(new NewFollower(Auth::user()->id, $userToFollow->id));
```


**Problem**
Listener: sends email notification of new follower.
Test will pass, even if listener does not fire (could be a simple typo).

**We can spy on the listener!**

```
//Arrange
$listener = Mockery::spy(EmailNewFollowerNotification::class); //the listener
//bind this in the IOC
app()->instance(EmailNewFollowerNotification::class, $listener);


```

```
//Assert
       $this->assertTrue($follower->follows($followed));
       $listener::shouldReceive('fire')->with(Mockery::on(function ($event) use ($follower, $followed) {
            return $event->followerId == $follower->id
            && $event->followedId == $followed->id;
        })->once();

```

This can test that the listener gets fired, but not what it actually does.





