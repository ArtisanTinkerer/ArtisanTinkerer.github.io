---
layout: post
title: "Databables - Lookup Field Felect "
date: 2016-02-19
---


# Populate a Select From A Joined Table

I never remember how to do this.

[Datatables Help](https://editor.datatables.net/manual/php/joins#Options)


Parameters - easy database options

The Field->options() method accepts up to five parameters:

string - The database table name that the options should be read from
string - The column name that contains the value for the list of options
string|array - The column(s) that contain the label for the list of options (i.e. this is what the user sees in the select list)

## This is the PHP
```
//Three parts
//1
    Field::inst( 'temp_records.area_id' )
                    ->options('areas','id','description', function ($q) {
                        $q->where('areas.deleted_at', null);
                    })
                    ->validator( 'Validate::dbValues' ),
     
 //2                 
     Field::inst( 'areas.description' ),
     
     
 //3 
       ->leftjoin('areas','areas.id','=','temp_records.area_id' )

```

## This is the JS

```
Editor:
{
						label: "Application:",
						name: "roles.application_id",
						type:"select",
						placeholder: "Select an Application"

					}


Table:
{ "data": "applications.name",editField:"roles.application_id"}

```





[Datatables Discussion](https://www.datatables.net/forums/discussion/32363/setting-a-where-in-options#latest)


