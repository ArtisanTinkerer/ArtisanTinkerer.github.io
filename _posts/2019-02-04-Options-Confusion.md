---
title: "Options-Confusion"
date: 2018-02-04
layout: default
---

I always struggle with this:


```
<select class="form-control" name="type">
      <option value = "" selected="true" disabled="disabled">Please select ...</option>
          @foreach($types as $typeid=>$typename)
              <option value="{{$typeid}}"  @if(old('type', $tenant->type ? $tenant->type : NULL) == $typeid) selected = 'selected'  @endif>{{$typename}}</option>
          @endforeach
  </select>


```

```
<option value="{{$typeid}}"  

//if we have an old value from failed validation, use that
//if we are editing, there will be a value in $tenant->type
// else use null
// then compare the result with the option id and set selected if a match

@if(old('type', $tenant->type ? $tenant->type : NULL) == $typeid) selected = 'selected'  


@endif>{{$typename}}</option>
```
