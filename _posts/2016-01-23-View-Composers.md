---
title: "View Composers"
date: 2018-03-20
layout: default
---

 - Create an  App\Http\ViewComposers directory
 
 ```
   public function boot()
    {
        view()->composer(
            'app',
            'App\Http\ViewComposers\NavbarComposer'
        );
    }
  
  ```

-  Add the service provider to the providers array in the  config/app.php configuration file.
-  Define the composer class:
  
