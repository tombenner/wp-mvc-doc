---
title: update_all
---
To update one or more fields of multiple records, use `update_all()`.  The first argument should be an array of the data that will be updated, and the second argument, which is optional, can be an array of options.  The commonly used option would be `conditions`, which would make the update only affect records that match the specified conditions.

{% highlight php %}
<?php

class Event extends MvcModel {
  
  public function make_past_events_not_public() {
    $this->update_all(
      array('is_public' => 0),
      array('date <' => date('Y-m-d'))
    );
  }
  
}

?>
{% endhighlight %}
