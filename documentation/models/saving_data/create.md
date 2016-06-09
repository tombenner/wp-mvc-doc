---
title: create
---
To create a record in the database for a model, call `create()`.  `create()` is most commonly used with data submitted from a form that was made using FormHelper:

{% highlight php %}
<?php
class AdminVenuesController extends AdminMvcController {

  public function add() {
    if (!empty($this->params['data']) && !empty($this->params['data']['Venue'])) {
      $object = $this->params['data']['Venue'];
      if (empty($object['id'])) {
        $this->Venue->create($this->params['data']);
        $id = $this->Venue->insert_id;
        $url = MvcRouter::admin_url(array('controller' => $this->name, 'action' => 'edit', 'id' => $id));
        $this->flash('notice', 'Successfully created!');
        $this->redirect($url);
      }
    }
    $this->set_object();
  }

}
?>
{% endhighlight %}

Please note that the workflow above can be handled behind the scenes using `create_or_save()`.
