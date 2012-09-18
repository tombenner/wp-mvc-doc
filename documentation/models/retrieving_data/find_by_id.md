---
title: find_by_id
---
This behaves almost identically to `find()`, except that it has two arguments: the first is an id, the second is the options array that `find()` uses.  It finds the record with a primary key value of the specified id, but also handles the options array in the same way that `find()` does.

{% highlight php %}
<?php
class VenuesController extends MvcPublicController {
  
  public function show() {
    $object = this->Venue->find_by_id($this->params['id'], array(
      'includes' => array('Event')
    ));
    $this->set('object', $object);
  }
  
}
?>
{% endhighlight %}