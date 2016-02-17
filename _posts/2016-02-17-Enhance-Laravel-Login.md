---
layout: post
title: "Extra Laravel Login Conditions"
date: 2016-02-17
---


Looked at this:

# http://laraveldaily.com/auth-login-how-to-check-more-than-just-emailpassword/

Copied postLogin from AuthenticatesUsers.php to AuthController

amended this bit:

```

if (Auth::attempt($credentials, $request->has('remember'))) {

            $gotPermissions =  AccessManager::getPermissions();

              if(!$gotPermissions){
                  Auth::logout();
                  return redirect('/auth/login')->withErrors(['username' =>  'You do not have access to this application.']);
              }


            return $this->handleUserWasAuthenticated($request, $throttles);
        }


```

Looks like it is working!



