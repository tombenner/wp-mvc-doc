---
title: mvc_get_plugins
---
This returns an array listing the currently active WP MVC-based plugins.

{% highlight php %}
<?php
// This will return an array that looks like the following:
// Array ( [0] => events-calendar-example [1] => hierarchical-documentation )
print_r(mvc_get_plugins());
?>
{% endhighlight %}