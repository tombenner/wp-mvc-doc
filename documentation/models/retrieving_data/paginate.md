---
title: paginate
---
`paginate()` is similar to `find()`, but it adds some functionality that is useful for creating paginated retrievals of data.  It returns a "collection," which is an array that contains the returned objects in the 'objects' key, but also contains information that is useful for creating pagination (total number of results, number of results per page, etc).

{% highlight php %}
<?php
class EventsController extends MvcPublicController {

  public function index() {
  
    $params = $this->params;
    $params['page'] = empty($this->params['page']) ? 1 : $this->params['page'];
    $params['conditions'] = array('is_public' => true);
    $collection = $this->model->paginate($params);
    $this->set('objects', $collection['objects']);
    $this->set_pagination($collection);
  
  }

}
?>
{% endhighlight %}