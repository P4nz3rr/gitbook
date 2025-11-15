---
description: >-
  Decrypts & strips Wi-Fi headers to make packet contents readable (wireshark).
  Removes wireless headers from unencrypted captures, Decrypt WEP with hex WEP
  key. Decrypt WPA/WPA2 (PSK) using passphrase.
---

# Airdecap-ng

<pre class="language-sh" data-title="# Remove Wireless Headers from Unencrypted Captures"><code class="lang-sh">sudo airdecap-ng <a data-footnote-ref href="#user-content-fn-1">-b</a> 00:D3:F5:7C:34:46 capture.cap
</code></pre>

<pre class="language-bash" data-title="# Decrypting WEP-encrypted captures"><code class="lang-bash">sudo airdecap-ng <a data-footnote-ref href="#user-content-fn-2">-w</a> 732483BC97393 OUTPUT-01.cap
</code></pre>

<pre class="language-bash" data-title="# Decrypting WPA-encrypted captures"><code class="lang-bash">sudo airdecap-ng <a data-footnote-ref href="#user-content-fn-3">-p</a> 'password' OUTPUT-01.cap <a data-footnote-ref href="#user-content-fn-4">-e</a> "APName"
</code></pre>

These commands for specific protocols will decrypt and allow for easy data analysis from outputted `-dec.cap` files.

[^1]: AP MAC Address

[^2]: WEP Key

[^3]: Password for AP

[^4]: ESSID of AP
