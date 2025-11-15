---
description: >-
  Enables wireless interface to capture all 802.11 frames within range, not just
  those addressed to it (unlike managed mode).  Provides full visibility of
  wireless traffic & supporting packet analysis.
---

# Airmon-ng

<pre class="language-bash" data-title="# Monitor Mode"><code class="lang-bash">sudo airmon-ng <a data-footnote-ref href="#user-content-fn-1">start</a> wlan0 11 # Specific Channel
</code></pre>

{% code title="# Check Interfering Processes" %}
```bash
sudo airmon-ng check
```
{% endcode %}

{% code title="# Kill Interfering Processes (If encountering problems)" %}
```bash
sudo airmon-ng check kill
```
{% endcode %}



[^1]: stop
