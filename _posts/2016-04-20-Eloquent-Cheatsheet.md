---
layout: default
title: "Eloquent Cheatsheet"
date: 2016-04-20
---

https://laravel.com/docs/5.1/eloquent

# Collections 

->all() 
->get()

     $targets = Target::where('week_no', $request->week_no)->get();

        foreach($targets as $target){
            $target->target = $request[$target->stream_id];
            $target->save();

        } 

# Single Models

::find(1);
->first();

# Two WHEREs

$loss = Loss::where('product_id', '=', $input['product_id'])->where('date_selected', '=', $input['date_selected'])->first();

# Relationship Notes


Working on my process loss system, I need to get all the fault buttons for the logged in user.
I think this will we *Has Many Through*.

User->Process Types->Faults

