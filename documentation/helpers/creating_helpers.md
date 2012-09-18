---
To create a helper, create a class in `app/helpers/` that extends `MvcHelper`.  For example, to create a helper named `DocumentationHelper`, we would create a file at `app/helpers/documentation_helper.php` will code like the following:

{% highlight php %}
<?php

class DocumentationHelper extends MvcHelper {
  
  public function parse_markdown($string) {
    static $parser;
    if (!isset($parser)) {
      $parser = new Markdown_Parser();
    }
    $string = $parser->transform($string);
    return $string;
  }
  
}

?>
{% endhighlight %}

The helper is now ready to be used.  To use it, you'll need to {% doc_link helpers load it in the controller %}.