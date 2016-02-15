---
layout: post
title: "JQuery Snippets"
date: 2016-02-15
---


# JQuery Snippets

I can never remember how to do bits and bobs in Jquery, so here they are:

## Set a value

```
 $("#best").val(0);
```
 
## Ajax!
 
``` 
    $.ajax({
            type: 'POST', // define the type of HTTP verb we want to use (POST for our form)
            url: '/records/store', // the url where we want to POST
            headers: {
                'X-CSRF-TOKEN': '{{ csrf_token() }}'
            },
            data: formData, // our data object
            dataType: 'json', // what type of data do we expect back from the server
            encode: true,
            success: function (data) {
                // success logic
                table.ajax.reload();
                $("#panel-head").notify("Record Added","success");
                clearForm()
                $('#part_no').focus();
            },

            error: function (data) {
                var errors = data.responseJSON;
                console.log(errors); //{"success":"false","0":{"part_no":"Not a valid product!"}}


            }
        });

```

## Retrive a number from an element
```
function getNum(val) {
    if (isNaN(val)) {
        val= 0;
    }

    if (val=="") {
        val =  0;
    }

    return parseInt(val);
}
```

## Select the text when the element receives focus
```

$(document).ready(function () {
    $("input").focus(function () {
        $(this).select();
    });
});
```

## Add class
```
$('#submit').addClass("btn-success");
$('#submit').removeClass("btn-success");
```






 
