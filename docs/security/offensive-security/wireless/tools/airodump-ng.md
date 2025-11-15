---
description: >-
  Captures raw 802.11 frames — used to collect WEP IVs and WPA/WPA2 handshakes
  for use with aircrack-ng.  Produces several output files (APs, clients,
  packets) containing detailed network info — useful
---

# Airodump-ng

{% code title="# To use Airodump-ng" %}
```shell
sudo airmon-ng start wlan0
```
{% endcode %}

<pre class="language-bash" data-title="# Scan APs &#x26; Clients"><code class="lang-bash">sudo airodump-ng <a data-footnote-ref href="#user-content-fn-1">-c 11</a> wlan0mon <a data-footnote-ref href="#user-content-fn-2">--band abg</a> <a data-footnote-ref href="#user-content-fn-3">-w WriteToFile...</a>
</code></pre>



[^1]: Specific or Multiple Channels (,)

[^2]: a -> 5 GHz

    b -> 2.4 GHz

    g -> 2.4 GHz

[^3]: Writes to file for data analysis
