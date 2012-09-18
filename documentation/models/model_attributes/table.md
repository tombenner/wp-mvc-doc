---
title: table
---
The name of the table which the model corresponds to.  A pluralized version of the model name with the current value of the WordPress database prefix$wpdb->prefix) is used by default (e.g. Venue will use a table named `wp_venues`).

If you set this value, you'll most likely want to include the token `{prefix} `at the beginning of the string, which will be replaced with the current value of $wpdb->prefix.  For example:

{% highlight php %}
<?php
class Venue extends MvcModel {

  var $table = '{prefix}my_venues';

}
?>
{% endhighlight %}