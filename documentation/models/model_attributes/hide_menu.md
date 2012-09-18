---
title: hide_menu
---
Each model shows up as an [Administration Menu](http://codex.wordpress.org/Administration_Menus) by default, by you can disable this menu by setting `hide_menu` to `false`.

{% highlight php %}
<?php
 
class Event extends MvcModel {
 
    var $hide_menu = false;
 
}
 
?>
{% endhighlight %}

For information on customizing Administration Menus, see {% doc_link configuration/adminpages %}.