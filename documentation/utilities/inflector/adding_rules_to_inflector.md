---
`MvcInflector` accounts for most nonstandard pluralizations (e.g. "person" to "people"), but you can add additional rules using `MvcInflect::rules()`.  These should typically be placed in `app/config/bootstrap.php`.

{% highlight php %}
<?php
MvcInflector::rules('singular', array(
    'rules' => array('/^(bil)er$/i' => '\1', '/^(inflec|contribu)tors$/i' => '\1ta'),
    'uninflected' => array('singulars'),
    'irregular' => array('spins' => 'spinor')
));
?>
{% endhighlight %}

{% highlight php %}
<?php
MvcInflector::rules('plural', array('irregular' => array('phylum' => 'phyla')));
?>
{% endhighlight %}