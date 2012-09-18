---
There is a default public layout and a default admin layout, but if you'd like to use, say, a different layout for some of the public views, that can easily be done (the same is true for admin views).  For example, to use a public layout named `'custom_layout'`, you would use:

{% highlight php %}
<?php
// controllers/venues_controller.php
class VenuesController extends MvcPublicController {
  
  public function show() {
    $this->set_object();
    $this->render_view('show', array('layout' => 'custom_layout'));
  }
  
}
?>

<?php // views/layouts/custom_layout.php ?>
<?php get_header(); ?>

<div class="page venues-show">

  <?php $this->render_main_view(); ?>

</div>

<?php get_footer(); ?>
{% endhighlight %}