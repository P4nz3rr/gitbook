# Authentication

<pre class="language-bash" data-title="# Basic Auth (GET)"><code class="lang-bash">curl -u user:password http://&#x3C;SERVER_IP>:&#x3C;PORT>/
curl http://user:password@&#x3C;SERVER_IP>:&#x3C;PORT>/ # Alternative to above
curl <a data-footnote-ref href="#user-content-fn-1">-H</a> 'Authorization: Basic uWiue76NhysNBgsid...=' http://&#x3C;SERVER_IP>:&#x3C;PORT>/ # Without credentials 
</code></pre>

<pre class="language-bash" data-title="# Basic Auth (POST)"><code class="lang-bash">curl -X POST <a data-footnote-ref href="#user-content-fn-2">-L</a> -d 'username=user&#x26;password=password' http://&#x3C;SERVER_IP>:&#x3C;PORT>/ <a data-footnote-ref href="#user-content-fn-3">-i</a>
curl <a data-footnote-ref href="#user-content-fn-4">-d</a> '{"data":"new-data"} '<a data-footnote-ref href="#user-content-fn-5">-b</a> 'PHPSESSID=al8r3kppr0...' -H 'Content-Type: application/json' http://&#x3C;SERVER_IP>:&#x3C;PORT>/ # Without credentials
</code></pre>

[^1]: We can authenticate with Authorization header value (v) directly instead of credentials.

[^2]: Follow Redirection: Some login forms redirect to another page (dashboard.html) after athentication.

[^3]: View cookie header

[^4]: Content-Type: application/json to be able to send JSON data.

[^5]: Can also use -H
