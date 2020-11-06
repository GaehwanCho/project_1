---
title: "How to apply google analytics to github blog?"
categories: tool
tags:
  - google analytics
  - github blog
---

1. create account & property

2. register Data Streams

3. set Data Streams

```html
<!-- Global site tag (gtag.js) - Google Analytics -->
<script
  async
  src="https://www.googletagmanager.com/gtag/js?id=<MEASUREMENT ID>"
></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag() {
    dataLayer.push(arguments);
  }
  gtag("js", new Date());

  gtag("config", "<MEASUREMENT ID>");
</script>
```

![ga_setting](/assets/img/GA_additional_setting.png "GA_setting")
