---
title: "Common-Faker-Carbon"
date: 2019-01-09
layout: default
---

## Faker

```

$faker->company,
$faker->word
$faker->randomElement([])
$faker->dateTime()
$faker->sentence

```

```

'thing_id' => factory(\App\Models\Thing::class)->create()->id


```


## Carbon
```
$current = Carbon::now();
$dt = Carbon::create(2012, 1, 31, 0);

$dt->toDateString();               // 2015-12-19
$startDate->toAtomString();

eq() equals
ne() not equals
gt() greater than
gte() greater than or equals
lt() less than
lte() less than or equals


```
