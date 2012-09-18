---
title: create_or_save
---
The `add` and `edit` actions in WP MVC's default admin controllers use `create_or_save()` to either create or update records using data submitted from a form.  `create_or_save()` checks `$this->params['data']` to see if data related to the controller's model is present.  If it is and an ID value is set, the record with that ID is updated; if it is and an ID is not set, a record is inserted with the submitted data.

{% highlight php %}
<?php

class AdminVenuesController extends MvcAdminController {

  public function add() {
    $this->create_or_save();
  }
  
  public function edit() {
    $this->verify_id_param();
    $this->create_or_save();
    $this->set_object();
  }

}

?>
{% endhighlight %}