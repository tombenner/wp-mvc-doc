---
title: update
---
To update one or more fields of a record, use `update()`.  The first argument should be the ID of the record, and the second argument should be an array of the data that will be updated.

{% highlight php %}
<?php

class Venue extends MvcModel {
  
  public function after_save($object) {
    $this->update_sort_name($object);
  }
  
  public function update_sort_name($object) {
    $sort_name = $object->name;
    $article = 'The';
    $article_ = $article.' ';
    if (strcasecmp(substr($sort_name, 0, strlen($article_)), $article_) == 0) {
      $sort_name = substr($sort_name, strlen($article_)).', '.$article;
    }
    $this->update($object->__id, array('sort_name' => $sort_name));
  }
  
}

?>
{% endhighlight %}