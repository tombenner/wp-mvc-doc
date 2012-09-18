---
Helpers provide reusable methods for displaying elements in views.  They should be loaded in controllers.  {% doc_link helpers/core_helpers Core helpers %} are loaded by default; to include any other helpers, you'll want to call `$this->load_helper()` in the controller.

For example, HtmlHelper is a core helper that is included by default, so to use it to create a link in a view, you would do something like this:

{% highlight php %}
<?php echo $this->html->link('Show all venues', array('controller' => 'venues', 'action' => 'index')); ?>
{% endhighlight %}

### Using a non-core helper

To use a helper that isn't a core helper, you'll just need to load it in the controller before using it in the view.

{% highlight php %}
<?php
// controllers/documentation_nodes_controller.php
class DocumentationNodesController extends MvcPublicController {
  
  public function show() {
    $this->load_helper('Documentation');
    $this->set_object();
  }

}

// views/documentation_nodes/show.php
echo $this->documentation->parse_markdown($object->content);
?>
{% endhighlight %}