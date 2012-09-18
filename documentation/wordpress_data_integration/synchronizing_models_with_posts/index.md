---
To be able to use all of WordPress's native post-related functionality with an MVC model, you can tell WP MVC to create a post for every object of a given model, and WP MVC will automatically update that post if the object is updated.

This allows you to more easily add model objects to [Navigation Menus](http://codex.wordpress.org/Navigation_Menus) (by adding the object's associated post to the menu; it will link to the object), set up commenting for that object (by setting up commenting on the object's associated post), etc.

There are three ways to configure this:

{% doc_children %}