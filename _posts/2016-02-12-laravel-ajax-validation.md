---
layout: post
title: "Validating an Ajax request"
date: 2016-02-15
---



# Validating an Ajax request

# The JS
I am using a Twitter Typeahead to enter the product code.
I want to validate when they leave the Typeahead.

```
 $( ".typeahead" ).blur(function() {
    //pop the part_no into variable
    var part_no = $( "#part_no").val();

    //check that we have a valid part_no
    $.ajax({
        type: 'GET',
        url: 'validateProduct',
        data:{part_no:part_no},
        headers: {
            'X-CSRF-Token': $('meta[name="_token"]').attr('content')
        },
        dataType: 'json', // what type of data do we expect back from the server
        encode: true,
        success: function (data) {
            // success logic
            $('#description').addClass("label label-default");
            $('#best').focus();

        },

        error: function (data) {
            var errors = data.responseJSON;
            //is this just a part_no error

            // Render the errors with js ...
            $('#description').text("Product Number is Invalid");
            $('#description').addClass("label label-danger");
            $('#part_no').focus();
        }
    });

    

});

```

## The Controller

```
        public function validateProduct(Request $request)
    {

        $this->validate($request, [
            'part_no' =>'exists:products,PART_NO'

            ]);

        return response()->json('success');

    }
    
```
    
    



