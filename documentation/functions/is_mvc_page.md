---
title: is_mvc_page
---
This simply returns a boolean signifying whether or not the current page is being rendered by a WP MVC-based plugin.

{% highlight php %}
<?php
echo is_mvc_page() ? 'WP MVC page!' : 'Not a WP MVC page!';
?>
{% endhighlight %}