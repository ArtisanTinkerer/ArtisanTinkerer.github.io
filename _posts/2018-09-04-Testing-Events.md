---
title: "Testing Events"
date: 2018-09-04
layout: default
---

## Firing Events
event(new AgreementCreated($agreement));


## Testing Them

### 1 Fake Them
```
      Event::fake();

        $this->PATCH("agreements/{$agreement->getRouteKey()}",
            ['type' => $type, 'user_group_id' => $customer->id, 'name' => 'changed']);

        Event::assertDispatched(AgreementUpdated::class);
        
```
