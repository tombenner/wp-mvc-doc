---
MvcFormTagsHelper can be used to create form input elements outside of the context of an object-based form (for which {% doc_link helpers/core_helpers/form the Form helper %} should be used).

For example:
{% highlight php %}
<?php
$html = '<form action="" method="post">';
$html .= MvcFormTagsHelper::text_input('title');
$html .= MvcFormTagsHelper::text_input('tagline', array('value' => 'A default value'));
$html .= MvcFormTagsHelper::checkbox_input('is_public', array('id' => 'public_checkbox', 'label' => 'Public'));
$html .= '<input type="submit" />';
$html .= '</form>';
echo $html;
?>
{% endhighlight %}

Its methods are:

* `input` - creates a text input by default, but if `'type'` is passed (e.g. `input('content', array('type' => 'textarea')`), that input type will be used instead
* `text_input`
* `textarea_input`
* `checkbox_input`
* `hidden_input`
* `select_input`
* `button`
