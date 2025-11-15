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

#### Automatic Request Modification

```bash
Proxy > Proxy settings > HTTP match and replace rules
```

#### Automatic Response Modification

```bash
Proxy > Options > Match and Replace
```

#### Repeating Requests (Repeater)

We can repeatedly send any request we intercepted in Burp.  &#x20;

```bash
Proxy > HTTP History # To send a request to repeater CTRL+R
```

#### Encoding/Decoding (Decoder)

{% code title="In Burp repeater select and right click on text then:" %}
```bash
Convert Selection > URL > URL-encode key characters
```
{% endcode %}

Burp has its own Decoded where we can encode and decode with many encoders (like Base64, Unicode). Moreover, Burp inspector can also be used inside the proxy and repeater tabs.

#### Burp's Fuzzer (Intruder)
