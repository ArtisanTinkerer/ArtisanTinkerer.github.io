---
title: "Starting to Mock"
date: 2016-01-23
layout: default
---

Mock a class
Maybe mock the MAADA
Then I need to move my code into a class somewhere.

Inject a mocked class, not the real one.
```
public function __construct(SlackClient $slack)
```

When testing:

```
$slackMock = Mockery::mock(SlackClient::class)->shouldIgnoreMissing();

//use the mocked one when you new up
$notifier = new Notifier($slackMock)


```
