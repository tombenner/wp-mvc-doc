---
title: primary_key
---
The name of the field which will be used as the primary key of an object.  The default value is `'id'`. 

{% highlight php %}
<?php

class Venue extends MvcModel {

  var $primary_key = 'id';

}

?>
{% endhighlight %}