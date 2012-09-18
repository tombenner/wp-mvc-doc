---
title: delete
---
To delete a specific record, pass its ID to `delete()`.

{% highlight php %}
<?php
class AdminVenuesController extends MvcAdminController {

  public function delete() {
    $this->set_object();
    if (!empty($this->object)) {
      $this->Venue->delete($this->params['id']);
      $this->flash('notice', 'Successfully deleted!');
    } else {
      $this->flash('warning', 'A venue with ID "'.$this->params['id'].'" couldn\'t be found.');
    }
    $url = MvcRouter::admin_url(array('controller' => $this->name, 'action' => 'index'));
    $this->redirect($url);
  }

}
?>
{% endhighlight %}