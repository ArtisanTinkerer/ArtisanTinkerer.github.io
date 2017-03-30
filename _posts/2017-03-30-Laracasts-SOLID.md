---
layout: default
title: "Laracasts-SOLID"
date: 2017-03-30
---

# Single Responsibility
S in SOLID - single responsibility

"A class should have one, and only one, reason to change"

"A class should have one job"

## Examples:
**Sales reporter should not have authentication in "extract to controller"**

**Querying the db and doing a calculation.**

**Formatting output.**

Class would have to change, if we need to change either of these.

*This violates single responsibility*

## How Fixed

**Querying the db and doing a calculation.**
This was moved to a repository.

**Formatting output.**

1, Leave this to the consumer.

This is not the sales reporters job, so this means it needs to go.

2,

In the Reporting folder, create an interface.

```
interface SalesOutputInterface
{

  public function output($sales);
  

}

//and output classes which implement this

class HtmlOutput implements SalesOutputInterface {

  public function output()
  {
    return "<h1>$sales</h1>";
  }

}

```

# Open Closed



