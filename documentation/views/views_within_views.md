---
To render a view within a view, use `$this->render_view()`.  For example, to render a view named `_tree.php` in the views directory of the current controller:

{% highlight php %}
<?php
$this->render_view('_tree');
?>
{% endhighlight %}

To render a view from a specific directory, specify the path:
{% highlight php %}
<?php
$this->render_view('documentation_nodes/_tree');
?>
{% endhighlight %}

To pass variables into the view, use:
{% highlight php %}
<?php
// index.php
$this->render_view('_tree', array('locals' => array('objects' => $tree_objects)));

// _tree.php
// This will print_r() the $tree_objects that was set in index.php
print_r($objects);
?>
{% endhighlight %}

There is a naming convention that views that are used as partials (i.e. small, basic views that are only rendered inside of larger views) should have file names that are prefixed with an underscore (like the `_tree.php` above).  (This convention is borrowed from Rails.)