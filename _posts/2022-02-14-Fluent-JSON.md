---
title: "Fluent-JSON"
date: 2022-02-14
layout: default
---



# pass a closure to assertJson

```
$response = $this->getJson('/users/1');
 
    $response
        ->assertJson(fn (AssertableJson $json) =>
            $json->where('id', 1)
                 ->where('name', 'Victoria Faith')
                 ->missing('password')
                 ->etc()
        );
        
        
        ```
