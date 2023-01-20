---
title: ADT XML layouts
date: 2013-02-02T11:11:19+00:00
---

So I've been fiddling around with ADT for a couple of hours. It's possible to programmatically create layouts; i.e., an Android UI, but it's not great. It's way easier to define the layout in XML, and then bind whatever event handlers are required. Here we have a simple class:

```java
package net.waynekhan.blog.foo;

import android.app.Activity;
import android.os.Bundle;
import android.view.*;
import android.widget.*;
import java.util.*;

public class HWA extends Activity implements View.OnClickListener {
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    setContentView(R.layout.main);
    Button b = (Button) findViewById(R.id.b);
      b.setOnClickListener(this);
  }

  public void onClick(View v) {
    switch (v.getId()) {
      case R.id.b: {
        Button b = (Button) v;
        b.setText(new Date().toString()); break;
      }
    }
  }
}
```

As you can see, it's quite bare. Load an XML layout `R.layout.main`, define a button `R.id.b`, then bind a click listener to the button.

Then we have `onClick()` to set button text to the current `String`-ified date. Our code is really clean, and we do all the UI-related stuff in `/res/layout/main.xml`, and put all our conveniently l10n strings in `/res/values/strings.xml`.
