---
title: flash
---
Use `flash()` to set a message or warning that will be displayed to the user.  The text will be displayed by `display_flash()`, which is called in the default admin layout (`views/admin/layouts/admin.php`), but can be called elsewhere if desired.

{% highlight php %}
<?php

// controllers/admin/admin_venues_controller.php

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

<?php
// views/admin/layouts/admin.php
?>

<div class="wrap">

<?php $this->display_flash(); ?>

<?php $this->render_main_view(); ?>

</div>

{% endhighlight %}