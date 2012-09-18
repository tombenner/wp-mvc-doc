---
title: database
---
If you're using multiple databases under the same MySQL connection, you can specify that a model's table is in a database other than the primary WordPress database using `$database`.  For example:

{% highlight php %}
<?php
class Venue extends MvcModel {

  var $database = 'shared_database';

}
?>
{% endhighlight %}