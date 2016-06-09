---
title: pagination
---
To create pagination links in a view, use `$this->pagination();`.  This needs to be called after `paginate()` and `set_pagination()` calls, as shown below, have been made in the controller.

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

`$this->pagination()` simply returns `paginate_links($this->pagination);`, where [`paginate_links()`](http://codex.wordpress.org/Function_Reference/paginate_links) is a WordPress function.  So, to modify the output behavior of the pagination links, either modify `$this->pagination` (which is set in `$this->set_pagination()` or just use `paginate_links()` directly.
