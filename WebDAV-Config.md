To load a WebDAV-located file from the web app, CORS must be enabled on your server.

❗ OPTIONS request must work **without** authorization.

Here's a config example:

For Apache:
```
Header always set Access-Control-Allow-Origin "*"
Header always set Access-Control-Allow-Headers "origin, content-type, cache-control, accept, authorization, if-match, destination, overwrite"
Header always set Access-Control-Expose-Headers "ETag"
Header always set Access-Control-Allow-Methods "GET, HEAD, POST, PUT, OPTIONS, MOVE, DELETE, COPY, LOCK, UNLOCK"
Header always set Access-Control-Allow-Credentials "true"

RewriteEngine on
RewriteCond %{REQUEST_METHOD} OPTIONS
RewriteRule ^(.*)$ blank.html [R=200,L,E=HTTP_ORIGIN:%{HTTP:ORIGIN}]
```

For nginx:
```
add_header 'Access-Control-Allow-Origin' '*';
add_header 'Access-Control-Allow-Credentials' 'true';
add_header 'Access-Control-Allow-Methods' 'GET, HEAD, POST, PUT, OPTIONS, MOVE, DELETE, COPY, LOCK, UNLOCK';
add_header 'Access-Control-Allow-Headers' 'Authorization,DNT,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,X-Accept-Charset,X-Accept,origin,accept,if-match,destination,overwrite';
add_header 'Access-Control-Expose-Headers' 'ETag';
add_header 'Access-Control-Max-Age' 1728000;
if ($request_method = 'OPTIONS') {
  add_header 'Content-Type' 'text/plain charset=UTF-8';
  add_header 'Content-Length' 0;
  add_header 'Access-Control-Allow-Origin' '*';
  add_header 'Access-Control-Allow-Credentials' 'true';
  add_header 'Access-Control-Allow-Methods' 'GET, HEAD, POST, PUT, OPTIONS, MOVE, DELETE, COPY, LOCK, UNLOCK';
  add_header 'Access-Control-Allow-Headers' 'Authorization,DNT,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,X-Accept-Charset,X-Accept,origin,accept,if-match,destination,overwrite';
  add_header 'Access-Control-Expose-Headers' 'ETag';
  add_header 'Access-Control-Max-Age' 1728000;
  return 204;
}
```

For caddy:
```
your.domain.com {
  basicauth /realurl user password
  webdav /realurl {
    scope /diskpath
  }
  cors / {
    origin *
    methods GET,HEAD,POST,PUT,OPTIONS,MOVE,DELETE,COPY,LOCK,UNLOCK,PROPFIND,MKCOL
    allow_credentials true
    max_age 1728000
    allowed_headers Authorization,DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,X-Accept-Charset,X-Accept,origin,accept,if-match,destination,overwrite
    exposed_headers ETag
  }
  rewrite /fake_url_for_kbdx  {
    if {method} not_is OPTIONS
    to /realurl/{path}
  }
  log /diskpathtolog
  errors /diskpathtoerrorlog
}
```

If you want KeeWeb to write files with PUT, instead of moving temporary file, you can change it with a switch in Settings &rarr; General.

## Custom certificates

If your WebDAV server is using a self-signed or invalid certificate, you can use this command to open files in KeeWeb desktop app:
```bash
certutil -d sql:$HOME/.pki/nssdb -A -t TC -n "my_domain.lan" -i ~/ca.crt
```
On Windows, adding your CA to trusted certificates storage may help.