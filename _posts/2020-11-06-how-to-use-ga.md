---
title: "How to apply google analytics to github blog?"
categories: tool
tags:
  - google analytics
  - github blog
toc: true
---

This post is about to apply [google analytics](https://analytics.google.com/) to github blog.  
Blog theme is [minimal-mistake](https://mmistakes.github.io/minimal-mistakes/).

## 1. create account & property

Create account & property. It's easy.

## 2. register Data Streams

After that, register data streams.  
Select `Data Streams` tab and click stream what you made.  
![](/project_1/assets/img/datastreams.png)

Click `Additional Settings -> Connected Site Tags`
![ga_setting](/project_1/assets/img/GA_setting.png "GA_setting")
Register your `<MEASUREMENT ID>`.

## 3. set Data Streams

Modify `google-gtag.html` file in your github page repo like below.  
The path is `_includes/analytics-providers/google-gtag.html`

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

Modify `_config.yml` `Analytics` part like below.

```yaml
# Analytics
analytics:
  provider: "google-gtag" # false (default), "google", "google-universal", "google-gtag", "custom"
  google:
    tracking_id: "<MEASUREMENT ID>"
    anonymize_ip: # true, false (default)
```
