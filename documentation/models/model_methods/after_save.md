---
title: after_save
---
To always process an object immediately after it is saved, define `after_save()`.

{% highlight php %}
<?php
class Venue extends MvcModel {
  public function after_save($object) {
    $this->update_sort_name($object);
  }
  
  // Use "Colosseum, The" instead of "The Colosseum" for the sort_name
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