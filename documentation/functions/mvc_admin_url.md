---
title: mvc_admin_url
---
This behaves like {% doc_link functions/mvc_public_url `mvc_public_url` %}, except that it provides the URL to admin MVC pages instead of public ones.  For example:

{% highlight php %}
<?php
// http://mysite.com/wp-admin/admin.php?page=mvc_venues
echo mvc_admin_url(array('controller' => 'venues'));

// http://mysite.com/wp-admin/admin.php?page=mvc_venues-add
echo mvc_admin_url(array('controller' => 'venues', 'action' => 'add'));

// http://mysite.com/wp-admin/admin.php?page=mvc_venues-edit&id=1
echo mvc_admin_url(array('controller' => 'venues', 'action' => 'edit', 'id' => 1));

?>
{% endhighlight %}