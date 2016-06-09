---
title: set_pagination
---
To allow for {% doc_link views/view_methods/pagination pagination links to easily be created in a view %}, call `$this->set_pagination($collection);` using a collection that is returned from a `paginate()` call on a model.  

{% highlight php %}
<?php
// controllers/venues_controller.php

class VenuesController extends PublicController {

  public function search() { 
    $collection = $this->Venue->paginate($this->params);
    $this->set('objects', $collection['objects']);
    $this->set_pagination($collection);
  }
  
}

// views/venues/search.php

echo $this->pagination();
?>
{% endhighlight %}


`set_pagination()` processes the collection and sets `$this->pagination` to an appropriate array that will be used in [`paginate_links()`](http://codex.wordpress.org/Function_Reference/paginate_links) within `$this->pagination();` in the view.
