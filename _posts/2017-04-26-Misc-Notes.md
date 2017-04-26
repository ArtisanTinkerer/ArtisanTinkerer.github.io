2017-04-26-Misc-Notes.md

---
layout: default
title: "Misc Notes"
date: 2017-04-26
---

# Scopes

## Global Scopes

*"Global scopes allow you to add constraints to all queries for a given model"*

```

class User extends Model
{
    /**
     * The "booting" method of the model.
     *
     * @return void
     */
    protected static function boot()
    {
        parent::boot();

        static::addGlobalScope(new AgeScope);
    }
}


```


## Local Scopes

Like this:

```
    public function scopePopular($query)
    {
        return $query->where('votes', '>', 100);
    }   
   
```


## In My Words

Global ones are hidden and will be activated just be doing User::all






