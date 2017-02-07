---
title: "Datatables MJoin"
date: 2017-02-7
layout: default
---

# Datatables One to Many Joins

[Datatables](https://editor.datatables.net/manual/php/mjoin)

I'm trying to add multiple data_sources to a widget, it looks like Mjoin will work.

Laravel uses link tables, in my case it's actually many to many.

*  A new Mjoin class is attached to an Editor instance using the Editor->join method 

like this:

```
->join(
        Mjoin::inst( 'access' )
            ->link( ... )
            ->order( ... )
            ->fields( ... )
    )
```

## Direct Link

## Link Table

** example **
staff -> staff_access -> access

** mine **
widgets -> data_source_widget -> data_sources


* The fields() method is used to define the two fields that will be read from the joined table: the id field which makes use of the options() method and also the name. The options() method for the id will obtain a list of options that the Javascript for Editor will use to populate the list of options based on the data available in the access table. This isn't required, but it does ensure data integrity! *

like this:

```
 ->join(
                Mjoin::inst( 'data_sources' )//table to link to
                ->link('widgets.id','data_source_widget.widget_id' ) //left table id, name in link table
                ->link('data_sources.id','data_source_widget.data_source_id' ) //right table id, name in link table

                ->order('data_sources.description asc')// order of joined data - optional
                ->fields(
                    Field::inst( 'id' ) //first field read from joined table
                    ->options( 'data_sources', 'id', 'description' )
                        ->validator( 'Validate::notEmpty' ),
                    Field::inst( 'description' ) //second field read from joined table
                )
            )
            ->process($postData)
            ->json();
```


I now have data_sources in the JSON.

## Client Side





