# HueBR Challenge 01

## Overview

This is my first web challenge called **HueBR Challenge 01**. Can you get the flag.html?

The flag.html is hosted by the latest Nginx version hosts with the following configuration.

```
server {
    listen 80;
    listen [::]:80;

    root /usr/share/nginx/html;
    index index.html index.htm index.nginx-debian.html;

    server_name _;

    location / {
        try_files $uri $uri/ =404;
    }

    if ( $request ~* "^GET /flag.html HTTP.*$" ){
        return 403;
    }
}
```

## Run

Git clone this repo and execute `docker-compose up`.

The flag.html will be available at http://localhost/flag.html.

## Tips

* No need to brute force anything.
* It's not a bug on Nginx.
* This could be also hosted in Apache with the following mod_rewrite rules.

```
    RewriteEngine On
    RewriteCond %{THE_REQUEST} "^GET /flag.html HTTP.*$" [NC]
    RewriteRule .* - [F]
```

## Contact

If you found the solution please send me the solution through [@riramar](https://twitter.com/ricardo_iramar) or ricardo.iramar@gmail.com and I'll include your name below.

## Solvers

No one yet.