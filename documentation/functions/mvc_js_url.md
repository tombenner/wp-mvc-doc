---
title: mvc_js_url
---
This returns the URL of a JavaScript file that's in the specified plugin's `app/public/` directory.  If a file extension isn't given, a `.js` is appended, but this automatic behavior can be bypassed by setting the `add_extension` option to `false`, as shown below.

{% highlight php %}
<?php
// This will return a URL that looks like the following:
// http://mysite.com/wp-content/plugins/events-calendar-example/app/public/js/my_script.js
echo mvc_js_url('events-calendar-example', 'my_script');

// This will prevent the ".js" from being appended:
// http://mysite.com/wp-content/plugins/events-calendar-example/app/public/js/my_script
echo mvc_js_url('events-calendar-example', 'my_script', array('add_extension' => false));
?>
{% endhighlight %}