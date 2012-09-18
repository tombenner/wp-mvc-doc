---
title: insert
---
Ideally, {% doc_link models/saving_data/create `create()` %} would be used to create records, but if you need to directly insert data, `insert()` can be used.  `insert()` behaves almost identically to [`$wpdb->insert()`](http://codex.wordpress.org/Class_Reference/wpdb#INSERT_rows), but it takes only one argument, the array of data that will be inserted into the model's table.