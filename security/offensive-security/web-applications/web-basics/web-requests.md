# Web Requests

#### <mark style="color:$success;">GET vs POST</mark>

GET requests are used for actions like searches or page access, while POST requests are used when transferring files or hiding parameters from the URL.

**Key differences:**

* **POST puts data in the request body**, GET in the URL.
* **Benefits:**
  1. **No logging issues:** Large uploads aren’t stored in logs like GET URLs.
  2. **Less encoding:** POST can send binary data; only separators need encoding.
  3. **More data:** POST isn’t limited by URL length (URLs usually < 2000 chars).

#### CRUD API

Not API's are the same technically, but the principles used are the same like in REST APIs.

| `Create` | `POST`   |
| -------- | -------- |
| `Read`   | `GET`    |
| `Update` | `PUT`    |
| `Delete` | `DELETE` |

<pre class="language-bash" data-title="# CREATE"><code class="lang-bash">curl -X POST http://&#x3C;SERVER_IP>:&#x3C;PORT>/endpoint.php/<a data-footnote-ref href="#user-content-fn-1">library</a>/ -d '{"book_name":"NEW_BOOK", "author_name":"AUTHOR_NAME"}' -H 'Content-Type: application/json'
</code></pre>

<pre class="language-bash" data-title="# READ"><code class="lang-bash">curl http://&#x3C;SERVER_IP>:&#x3C;PORT>/endpoint.php/library/<a data-footnote-ref href="#user-content-fn-2">book</a> | <a data-footnote-ref href="#user-content-fn-3">jq</a> # Retrieve specific entries
</code></pre>

<pre class="language-bash" data-title="# UPDATE (PUT)"><code class="lang-bash">curl -X PUT http://&#x3C;SERVER_IP>:&#x3C;PORT>/endpoint.php/library/<a data-footnote-ref href="#user-content-fn-2">book</a> -d '{"book_name":"NEW_BOOK", "author_name":"AUTHOR_NAME"}' -H 'Content-Type: application/json'
</code></pre>

`PATCH` is used to partially update an entry ("e.g. author\_name"), while `PUT` is used to update the entire entry.

<pre class="language-bash" data-title="# DELETE"><code class="lang-bash">curl -X DELETE http://&#x3C;SERVER_IP>:&#x3C;PORT>/endpoint.php/library/<a data-footnote-ref href="#user-content-fn-2">book</a> # Will delete entire entry
</code></pre>



[^1]: Table name

[^2]: Search item

[^3]: Format JSON correctly
