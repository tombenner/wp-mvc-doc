---
title: selects
---
By default, all of the columns of a model's table will be retrieved in a SELECT query, but you can change this default behavior by specifying an array of columns to select in `$select`.  For example:

{% highlight php %}
<?php
class Venue extends MvcModel {

  var $selects = array('id', 'name', 'url');

}
?>
{% endhighlight %}