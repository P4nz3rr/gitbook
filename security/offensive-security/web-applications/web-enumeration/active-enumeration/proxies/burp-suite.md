# Burp Suite

{% code title="Intercept a Request" %}
```bash
Proxy > Intercept On/Off # On by default
```
{% endcode %}

We can manipulate intercepted requests by testing for: SQL injections, Command injections, Upload bypass, Authentication bypass, XSS, XXE, Error handling, Deserialization.

{% code title="Intercept a Response" %}
```bash
Proxy > Proxy Settings > Enable Intercept Response # Now enable request interception again and force refresh the page CTRL+SHIFT+R
```
{% endcode %}

Now when we forward a request the response will also be intercepted in Burp. We can use intercepted responses to change the way a web page is rendered in our browser.&#x20;

**Example (To make this persistent see** Automatic Response Modificatio&#x6E;**)**

Lets say a web page field allows only numeric numbers to be inputted. We can change that by modifying the intercepted response HTML code in Burp by allowing type="number" to type="text". Now our browser will display the web page with the text will inputted in the field.

#### Request vs Response&#x20;

Being able to modify how a web page renders can make certain web application penetration tests significantly easier, removing the need to submit input through an intercepted request. We can **automate this process** so that response modifications occur automatically, eliminating the need for repeated manual interception and editing.

{% code title="Automatic Request Modification" %}
```bash
Proxy > Proxy settings > HTTP match and replace rules
```
{% endcode %}

{% code title="Automatic Response Modification" %}
```bash
Proxy > Options > Match and Replace
```
{% endcode %}

We can repeatedly send any request we intercepted in Burp.  &#x20;

{% code title="Repeating Requests (Repeater)" %}
```bash
Proxy > HTTP History # To send a request to repeater CTRL+R
```
{% endcode %}

{% code title="Encoding/Decoding (Decoder)" %}
```bash
Convert Selection > URL > URL-encode key characters # In Burp repeater select and right click on text then do this
```
{% endcode %}

Burp has its own Decoded where we can encode and decode with many encoders (like Base64, Unicode). Moreover, Burp inspector can also be used inside the proxy and repeater tabs.

#### <mark style="color:$danger;">Intruder</mark>

{% code title="Burp's Fuzzer (Intruder)" %}
```
Proxy History > Right click request > Send to intruder
```
{% endcode %}

_“_&#x50;osition&#x73;_”_ is where we mark the spot in the request that Burp Intruder will replace with payloads from our wordlist.

{% code title="Leave extra two lines at bottom of the request before fuzzing" %}
```bash
GET /§DIR§/ HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Accept: */*
```
{% endcode %}

In the Payloads tab, we choose the wordlist Burp Intruder will iterate through. Each line of the list is inserted into the Payload Position we marked earlier. Four settings matter: **Payload Position & Type, Payload Configuration, Payload Processing, Payload Encoding.**

<mark style="color:$danger;">**Payload Position & Type:**</mark>\
Because we’re using a **Sniper** attack with only one payload marker, we only have **Payload Set 1 – DIRECTORY**. If we used **Cluster Bomb** and multiple § positions, we’d get multiple payload sets.

We then choose the **Payload Type**, which controls how Intruder generates or reads payloads. Common options:

* **Simple List** – reads a wordlist line-by-line (most common).
* **Runtime File** – reads the file during the attack to reduce memory usage.
* **Character Substitution** – creates permutations by swapping characters.

Burp has many other types, but for directory fuzzing we use **Simple List**.

<mark style="color:$danger;">**Payload Configuration**</mark> depends on the **Payload Type**. For a **Simple List**, we need to supply a wordlist. We can: **Add** entries manually (building a list inside Burp), or **Load** a wordlist file from disk.

<mark style="color:$danger;">**Payload Processing**</mark> lets us apply rules to our wordlist before Intruder sends each payload. We can modify, filter, or extend entries—for example, adding file extensions or removing unwanted lines.

To filter out entries that start with a dot (`.`), we add a rule:

**Add → Skip if matches regex**

```bash
^..*$
```

<mark style="color:$danger;">**Payload Encoding**</mark> controls whether Burp URL-encodes the payloads before sending them.

A key feature for directory fuzzing is **Grep – Match**, which highlights responses based on patterns. Since we want to spot directories that return **200 OK**, we:

```bash
Enable Grep – Match > Click Clear > Add the string 200 OK > Disable Exclude HTTP headers (because the status code is in the header)
```

The entries starting with `.` will skip due to our regex rule. The results table will show each payload and the response status. Because we enabled **Grep – Match** for **200 OK**, the matching column will highlight successful hits. We can sort by **200 OK**, **Status**, or **Length** to bring interesting results to the top.

When the scan finishes, we will find one valid directory `/admin/` returning **200 OK**. We can manually check it in the browser to confirm.

Burp Intruder can fuzz or brute-force almost anything—directories, parameters, passwords, or even perform password spraying against AD-backed login portals (OWA, SSL VPNs, RDS, Citrix, custom apps, etc.).
