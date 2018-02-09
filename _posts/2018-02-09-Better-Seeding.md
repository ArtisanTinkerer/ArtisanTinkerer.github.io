---
title: "Better Seeding"
date: 2018-02-09
layout: default
---

Just wondering how I could seed my data better, especially for those pivot tables.

##
* Use DB Facade
* Use Model
* Use Model Factories

```
factory('App\User',50)->create([
  'name' => 'John Doe'
]);

```

Maybe
1, seed groups
2, seed users - assigned to groups

Or Maybe this should all be done in users and groups seeder.

