To use WebDAV-located file from web app, CORS must be enabled on your server. Here's an example of config:

For Apache:
```
Header always add Access-Control-Allow-Origin "*"
Header always set Access-Control-Allow-Headers "origin, content-type, accept, authorization, if-match, destination, overwrite"
Header always set Access-Control-Expose-Headers "ETag"
Header always set Access-Control-Allow-Methods "GET, HEAD, POST, PUT, OPTIONS, MOVE, DELETE, COPY, LOCK, UNLOCK"
Header always set Access-Control-Allow-Credentials "true"

RewriteEngine on
RewriteCond %{REQUEST_METHOD} OPTIONS
RewriteRule ^(.*)$ blank.html [R=200,L,E=HTTP_ORIGIN:%{HTTP:ORIGIN}]
```

For nginx:
```
if ($request_method = 'OPTIONS') {
    add_header 'Access-Control-Allow-Origin' '*';
    add_header 'Access-Control-Allow-Credentials' 'true';
    add_header 'Access-Control-Allow-Methods' 'GET, HEAD, POST, PUT, OPTIONS, MOVE, DELETE, COPY, LOCK, UNLOCK';
    add_header 'Access-Control-Allow-Headers' 'Authorization,DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,X-Accept-Charset,X-Accept,origin,accept,if-match,destination, overwrite';
    add_header 'Access-Control-Expose-Headers' 'ETag';
    add_header 'Access-Control-Max-Age' 1728000;
    add_header 'Content-Type' 'text/plain charset=UTF-8';
    add_header 'Content-Length' 0;
    return 204;
}

add_header 'Access-Control-Allow-Origin' '*';
add_header 'Access-Control-Allow-Credentials' 'true';
add_header 'Access-Control-Allow-Methods' 'GET, HEAD, POST, PUT, OPTIONS, MOVE, DELETE, COPY, LOCK, UNLOCK';
add_header 'Access-Control-Allow-Headers' 'Authorization,DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,X-Accept-Charset,X-Accept,origin,accept,if-match,destination, overwrite';
add_header 'Access-Control-Expose-Headers' 'ETag';
add_header 'Access-Control-Max-Age' 1728000;
```