---
layout: default
title: "Password Resets with Username"
date: 2017-08-21
---

I use usernames to login, because some of my users don't have e-mail addresses (password resets go to their managers).

This means making the following changes:

```
 ForgotPasswordController.php
 ResetPasswordController.php
 auth.php
 login.blade.php
 email.blade.php
 reset.blade.php
```

### Controllers
This just means copying the method from the trait and swapping the email for username.

### Views
Just swap the email fields for username.



