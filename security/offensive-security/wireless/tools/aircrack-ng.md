---
description: >-
  Offline cracking tool that uses captured packets to crack WEP and WPA/WPA2
  (PSK and PMKID); no live interaction with the Wi-Fi device required.
---

# Aircrack-ng

{% code title="# Benchmark to assess CPU performance for cracking " %}
```bash
aircrack-ng -S
```
{% endcode %}

<pre class="language-bash" data-title="# Cracking WEP"><code class="lang-bash">aircrack-ng <a data-footnote-ref href="#user-content-fn-1">-K</a> OUTPUT.ivs 
</code></pre>

Above command recovers WEP keys once enough IVs are captured. Use `airodump-ng --ivs` to save only IVs, then run `aircrack-ng -K` to apply the Korek WEP-cracking method.

{% code title="# Cracking WPA" %}
```bash
aircrack-ng OUTPUT.pcap -w passwords.txt
```
{% endcode %}

Cracks WPA/WPA2-PSK from a captured four-way handshake (capture with airodump-ng).

* Cracking uses a dictionary/wordlist (offline).
* A full handshake is 4 EAPOL packets, but Aircrack-ng can work with just packets 2+3 or 3+4.



[^1]: Korak WEP-cracking method
