---
layout: post
title: "Select2 Autocomplete with AJAX source in a Datatable"
date: 2016-03-14
---

I'm struggling to get this working.

I'm writing a new system (Process-Loss) which will be used in our factory. 
Users will capture fault information using tablets.

I need a screen to associate available faults with processess. This is so that only certain faults are available for associated processes.
The editor for this screen needs to use an autocomplete field withing a Datatables Editor.

This should be similar to using a normal select. This is how I do that:

## Editor Setup
```
{
					label: 'Input Type:',
					name: 'process_types.input_type_id',
					type:'select',
          placeholder: 'Select an Input Type'
}

```
The id is the field I need to update in the db.

## Table Setup

```
{ 'data': 'input_types.description',editField:'process_types.input_type_id'}
```

This is in the columns array. Description is what I want to display, id is the edit field.

## PHP

```

//Dont forget the join
//this is how to do a select //this table.foreign key
Field::inst( 'process_types.input_type_id' )
//joined table fields
  ->options('input_types','id','description')
  ->validator( 'Validate::dbValues' ),
//joined table.field to display
  Field::inst('input_types.description')
  //joined table, id, foreign key in this table
  )->leftjoin('input_types', 'input_types.id', '=', 'process_types.input_type_id')
```


Let's walk through this:

```Field::inst( 'process_types.input_type_id' )``` This is the field I want to edit.

```->options('input_types','id','description')``` These are the fields for the select, from the joined table.

```Field::inst('input_types.description')```  This is the field from the joined table which I want to display.


And the bit I always forget:
```
)->leftjoin('input_types', 'input_types.id', '=', 'process_types.input_type_id')
```
Just a join to the table which holds the descriptions.
Need to link the foreign key in the left table to the primary in the right.


I'm going to try this for my Select2 and see how it goes.








