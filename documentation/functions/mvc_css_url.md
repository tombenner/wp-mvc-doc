---
title: mvc_css_url
---
This returns the URL of a CSS style sheet that's in the specified plugin's `app/public/` directory.  If a file extension isn't given, a `.css` is appended, but this automatic behavior can be bypassed by setting the `add_extension` option to `false`, as shown below.

{% highlight php %}
<?php
// This will return a URL that looks like the following:
// http://mysite.com/wp-content/plugins/events-calendar-example/app/public/css/my_style.css
echo mvc_css_url('events-calendar-example', 'my_style');

// This will prevent the ".css" from being appended:
// http://mysite.com/wp-content/plugins/events-calendar-example/app/public/css/my_style
echo mvc_css_url('events-calendar-example', 'my_style', array('add_extension' => false));
?>
{% endhighlight %}