---
description: >-
  Hidden SSID appear less visible, but this offers only minimal security, as
  hidden SSIDs can still be discovered.
---

# Hidden SSIDs

<pre class="language-bash" data-title="# Set interface to Monitor"><code class="lang-bash">sudo airmon-ng <a data-footnote-ref href="#user-content-fn-1">start</a> wlan0
</code></pre>

[Airodump-ng](tools/airodump-ng.md) will show hidden SSIDs; `<length: x>` indicates the SSID length.

To reveal hidden SSIDs:

* If clients are connected, use [**aireplay-ng**](tools/aireplay-ng.md) to deauth them. When they reconnect, **airodump-ng** captures (will show) the SSID.
* WPA3 networks resist deauth attacks due to 802.11w (PMF); brute-force attacks may be needed instead.

#### Detecting Hidden SSID using Deauth

```bash
sudo aireplay-ng -0 10 -a F5:D2:00:AF:69:67 -c D5:00:B2:AF:23:24 wlan0mon
```

#### Bruteforcing Hidden SSID

<pre class="language-bash"><code class="lang-bash">sudo mdk3 wlan0mon <a data-footnote-ref href="#user-content-fn-2">p</a> <a data-footnote-ref href="#user-content-fn-3">-b</a> <a data-footnote-ref href="#user-content-fn-4">u</a> <a data-footnote-ref href="#user-content-fn-5">-c</a> 1 <a data-footnote-ref href="#user-content-fn-6">-t</a> A2:FF:31:2C:B1:C4
</code></pre>

#### **Bruteforcing using a Wordlist**

<pre class="language-bash"><code class="lang-bash">sudo mdk3 wlan0mon <a data-footnote-ref href="#user-content-fn-2">p</a> <a data-footnote-ref href="#user-content-fn-7">-f</a> passwords.txt <a data-footnote-ref href="#user-content-fn-6">-t</a> A2:FF:31:2C:B1:C4
</code></pre>



[^1]: stop

[^2]: Basic probing and ESSID Bruteforce mode

[^3]: test-option: Use full brute-force mode

[^4]: Options for brute-force mode:



    upper case (u)

    digits (n)

    all printed (a)

    lower and upper case (c)

    lower and upper case plus numbers (m)

[^5]: channel

[^6]: Target AP

[^7]: test-option: Wordlist Mode
