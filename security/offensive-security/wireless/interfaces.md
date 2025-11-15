---
description: >-
  Wi-Fi interfaces have different modes, each enabling specific capabilities in
  wireless communications. What each mode does.  How to test if your interface
  supports it:
---

# Interfaces

{% code title="# Check interface strength" %}
```bash
iwconfig
iw reg get
```
{% endcode %}

{% code title="# Change interface region (Abide by pertinent rules and laws when changing)" %}
```bash
sudo iw reg set US
```
{% endcode %}

{% code title="# Change interface power settings" %}
```bash
sudo ifconfig wlan0 down
sudo iwconfig wlan0 txpower 40
sudo ifconfig wlan0 up
```
{% endcode %}

{% code title="# Check interface capabilities" %}
```bash
iw list
```
{% endcode %}

{% code title="# Change interface channel" %}
```bash
sudo ifconfig wlan0 down
sudo iwconfig wlan0 channel 64
sudo ifconfig wlan0 up
iwlist wlan0 channel
```
{% endcode %}

{% code title="# Change interface frequency" %}
```bash
sudo ifconfig wlan0 down
sudo iwconfig wlan0 freq "5.52G"
sudo ifconfig wlan0 up
```
{% endcode %}

{% code title="# Check frequency" %}
```bash
iwlist wlan0 frequency | grep Current
```
{% endcode %}

<pre class="language-sh" data-title="# Change mode to managed"><code class="lang-sh">sudo iwconfig wlan0 mode <a data-footnote-ref href="#user-content-fn-1">managed</a>
</code></pre>

{% code title="# Broadcast a network on master mode" %}
```bash
interface=wlan0
driver=65782yn
ssid=APName
channel=7
hw_mode=g

sudo hostapd open.conf
```
{% endcode %}

{% code title="# Change interface to mesh mode" %}
```bash
sudo iw dev wlan0 set type mesh
```
{% endcode %}

{% code title="# Change interface to monitor mode (First disable interface)" %}
```bash
sudo iw wlan0 set monitor control
```
{% endcode %}

#### **Wi-Fi Attack Modes and Interface Requirements**

1. **Rogue AP / Evil-Twin Attack**
   * Requires **master/AP mode** support.
   * Tools/daemons: `hostapd`, `hostapd-mana`, `hostapd-wpe`, `airbase-ng`.
   * Purpose: Set up a fake access point to trick clients into connecting.
2. **Backhaul / Mesh Exploitation**
   * Requires **ad-hoc or mesh mode** support.
   * Basic monitoring: **monitor mode + packet injection** is often enough.
   * Advanced: Allows **node impersonation** and other mesh/network-level attacks.

[^1]: adhoc
