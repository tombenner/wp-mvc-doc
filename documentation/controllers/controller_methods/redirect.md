---
title: redirect
---
To redirect to another page while inside of a controller, use `redirect()`.

{% highlight php %}
<?php
$url = MvcRouter::admin_url(array('controller' => 'venues', 'action' => 'index'));
$this->redirect($url);
?>
{% endhighlight %}