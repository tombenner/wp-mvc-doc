---
title: AdminPages
---
By default, an admin controller has three admin pages (other than the parent index page): add, edit, and delete, but this list can be modified by appending an array to MvcConfiguration's 'AdminPages' setting.

A page can either be defined by a string (e.g. `'custom_page'` below) or with an array (e.g. `'another_page'` below) that can have the following options:

* `label` - The title of the page that shows up in the menu
* `in_menu` - Whether the page is displayed in the menu (default: true)
* `parent_slug` - Set this to place the link to this page in a different admin menu (e.g. 'tools.php' for Tools) (see [add_submenu_page](http://codex.wordpress.org/Function_Reference/add_submenu_page) for details) (default: null)

{% highlight php %}
<?php

MvcConfiguration::append(array(
  'AdminPages' => array(
    'speakers' => array(
      'add',
      'delete',
      'edit',
      'custom_page',
      'another_page' => array(
        'label' => 'Another Page',
        'in_menu' => false,
        'parent_slug' => 'tools.php'
      )
    )
  )
));

?>
{% endhighlight %}