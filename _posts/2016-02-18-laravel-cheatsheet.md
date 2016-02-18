---
layout: post
title: "Laravel Cheatsheet"
date: 2016-02-18
---

# Add Table

php artisan make:migration create_users_table
php artisan make:migration create_users_table --create=users

# Modify

php artisan make:migration add_votes_to_users_table --table=users


# Make Model
php artisan make:model User

# Get All

$flights = Flight::all();

# Make a select from a table
## Controller
```
$selectors = Selector::lists( 'description','id');
return view('datatables.records.list',compact('buttons','edit','selectors','areas'));
```

##Model
```
{!! Form::label('area_id', 'Area:', ['class' => 'col-sm-1 form-control-label']) !!}
<div class="col-sm-2">
      {!! Form::select('area_id', $areas,null, array('class' => 'form-control')) !!}
</div>
                

```
