---
If an association is set as being dependent, when the parent object is deleted, all of the associated objects that belong to it will be deleted, too.

In the following example, if a List object is deleted, all of its ListItems will be deleted, too.

{% highlight php %}
<?php
class List extends MvcModel {

  var $has_many = array(
    'ListItem' => array(
      'dependent' => true
    )
  );

}
?>
{% endhighlight %}