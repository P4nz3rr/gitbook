# Fuzzing

### Directory & File Fuzzing

```bash
ffuf -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u http://IP:PORT/FUZZ
```

<pre class="language-bash" data-title="Fuzz for files within a directory"><code class="lang-bash">ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt -u http://IP:PORT/directory/FUZZ <a data-footnote-ref href="#user-content-fn-1">-e</a> .php,.bak -v <a data-footnote-ref href="#user-content-fn-2">-fc</a> 404,403
</code></pre>

[^1]: -x for feroxbuster!

[^2]: Filter specific response codes
