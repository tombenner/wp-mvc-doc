---
title: per_page
---
The default number of results per page that are returned when paginate() is called on the model.  For example:

{% highlight php %}
<?php
class Venue extends MvcModel {

  var $per_page = 8;

}
?>
{% endhighlight %}