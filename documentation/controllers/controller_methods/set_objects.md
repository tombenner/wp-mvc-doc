---
title: set_objects
---
In an action that will show a collection of objects (e.g. the conventional `index` action), calling `$this->set_objects()` will find a paginated collection of the objects from the controller's native model and make it available to the view as `$objects` (using the equivalent of `$this->set('objects', $objects)`).

`set_objects()` will handle pagination behind the scenes.  If a URL param named `page` (or in an admin action a URL named `page_num`) is set, `set_objects()` will use that to properly paginate the collection.  It also calls `$this->set_pagination($collection);`, which will allow for {% doc_link views/view_methods/pagination pagination links to be displayed in the view %}.

{% highlight php %}
<?php
// controllers/venues_controller.php
class VenuesController extends MvcPublicController {
  
  public function index() {
    $this->set_objects();
  }
  
}

// views/venues/index.php
// This will print_r() all of the retrieve objects
print_r($objects);
?>
{% endhighlight %}