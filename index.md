---
layout: default
title: Home
---

### An MVC Framework for WordPress

WP MVC is an MVC framework that makes WordPress development faster, easier, and more elegant. It is a full-fledged framework with conventions that are similar to those of Ruby on Rails and CakePHP. Developers can consequently use it to rapidly build sites that take advantage of both WordPress's native functionality and vast plugin library and all of the many advantages of an MVC framework. 

WordPress supports a number of specific content types natively, but setting up custom post types and all of the necessary related functionality (public views, administrative management, associations, etc) is typically more time-consuming than doing the equivalent work in an MVC framework. The resulting code and database structure is significantly less graceful than the MVC equivalent, too.

WP MVC fills this gap. The basic idea is that you create an app/ directory that contains a file structure similar to other MVC frameworks (controllers/, helpers/, models/, views/, etc) and set up models, views, and controllers just as you would in other frameworks. WP MVC runs this code in the context of WordPress (i.e. you can still use all of WordPress's functionality inside of app/). Since WordPress already provides an administrative system, admin actions and views in app/ are run in that context, with WP MVC adding all of the necessary WordPress actions and filters to make this possible without the developer needing to lift a finger. An [Administration Menu](http://codex.wordpress.org/Administration_Menus) is automatically created for each model, but it can be customized or omitted.