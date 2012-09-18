---
title: save
---
To save a record in the database for a model, call `save()`.  `save()` will check for the presence of the model's primary key; if it is present, it will update the record with that ID; if it isn't present, it will create a new record.  `save` is most commonly used with data submitted from a form that was made using FormHelper:

{% highlight php %}
<?php
class AdminVenuesController extends AdminMvcController {

  public function edit() {
    if (!empty($this->params['data']) && !empty($this->params['data']['Venue'])) {
      $object = $this->params['data']['Venue'];
      if ($this->Venue->save($this->params['data'])) {
        $this->flash('notice', 'Successfully saved!');
        $this->refresh();
      } else {
        $this->flash('error', $this->Venue->validation_error_html);
      }
    }
    $this->set_object();
  }

}
?>
{% endhighlight %}

Please note that the workflow above can be handled behind the scenes using `create_or_save()`.