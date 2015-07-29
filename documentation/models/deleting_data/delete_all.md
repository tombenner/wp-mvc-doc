---
title: delete_all
---
To delete all records that match given conditions, use `delete_all()`.

{% highlight php %}
<?php

class Event extends MvcModel {
  
  public function delete_past_events() {
    $this->delete_all( array(
            'conditions' =>  array('date <' => date('Y-m-d')
                ))
    );
  }
  
}

?>
{% endhighlight %}
