---
title: find_one
---
This behaves almost identically to `find()`, except that it only returns a single object instead of an array of objects.

{% highlight php %}
<?php
class VenuesController extends MvcPublicController {
  
  public function show() {
    $object = this->Venue->find_one(array(
      'slug' => $this->params['slug'],
      'includes' => array('Event')
    ));
    $this->set('object', $object);
  }
  
}
?>
{% endhighlight %}