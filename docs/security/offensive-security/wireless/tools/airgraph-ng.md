---
description: >-
  Visualizes CSV outputs from Airodump-ng.  Generates two key graph types:
  (CAPR) Displays connections between clients and access points. (CPG)
  Visualizes networks probed by clients, connected or not.
---

# Airgraph-ng

{% code title="# Client to AP Relationship" %}
```bash
sudo airgraph-ng -i OUTPUT-01.csv -g CAPR -o CAPR.png
```
{% endcode %}

{% code title="# Common Probe Graph" %}
```bash
sudo airgraph-ng -i OUTPUT-01.csv -g CPG -o CPG.png
```
{% endcode %}
