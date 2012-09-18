---
A layout contains the code for generating HTML that wraps around the main view.  A WP MVC plugin uses at least two layouts: one for the public views and one for the admin views.  Default versions of these layouts are included in WP MVC core, though, so you only need to add them to your plugin if you want to use layouts that differ from these defaults.

A plugin's custom public layout would be at `views/layouts/public.php`, and it's custom admin layout would be at `views/admin/layouts/admin.php`.

The default public layout is:

{% highlight php %}
<?php get_header(); ?>

<?php $this->render_main_view(); ?>

<?php get_footer(); ?>
{% endhighlight %}

The default admin layout is:

{% highlight php %}
<div class="wrap">

<?php $this->display_flash(); ?>

<?php $this->render_main_view(); ?>

</div>
{% endhighlight %}

You can use any code in a layout that you would use in a view.  For example, we could render a couple of views in addition to the main view:

{% highlight php %}
<?php get_header(); ?>

<?php $this->render_view('_search_form'); ?>

<div class="page">

  <div id="single-body" class="post-body">

    <?php $this->render_view('_tree', array('locals' => array('objects' => $tree_objects))); ?>
    
    <div id="documentation_container">
    
      <?php $this->render_main_view(); ?>
    
    </div>
  
  </div>

</div>

<?php get_footer(); ?>
{% endhighlight %}