--- 
layout: post
title: Single Responsibilty, How Did I Forget You
---
Sometimes when developing I forget some of the basics as I go along. This time and many times in the past I have forgotten to follow the [Single Responsibility Principle](http://en.wikipedia.org/wiki/Single_responsibility_principle). I always forget it in the same place, the User object.

The User class always appears to be a place to take care of login and logout, but it does so much more. Everytime I need to change the User or expand to multiple types I end up dealing with login issues. It is easy to think that the responsibility of the User is to handle all things related to the User, but logins are not part of the User. The login is the responsibility of the Credentials.

What happens when I need multiple logins to act on behalf of the same user, or when I have multiple user types, but I want to use the same login system. In the past I've always created a User and an AdminUser, with separate logins. Why?...It just felt right, and the AdminUser had different properties than a regular user. Now I have multiple user types that should share some common code. Sweet, a module will do that for me. It still doesn't solve all of my issues. I have to separate logins. What should I have done?

A Credential class should be created and can link to a profile. This allows my Credential class to only change if the login system changes. Each user type can be a separate Profile class. This eases the burden of the user class and allows greater future expandability.

Why didn't I do this in the past? I've run into this problem many times, but never really got it. Now I'd just like to say, "I GET IT!!!"