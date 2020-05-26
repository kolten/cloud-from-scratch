# Ghost
Ghost is a free and open source blogging platform written in JavaScript and distributed under the MIT License, designed to simplify the process of online publishing for individual bloggers as well as online publications.

https://hub.docker.com/_/ghost

```
$ mkdir ~/ghost
$ vim ~/Caddyfile

https://example.com {
        file_server {
                root /usr/share/caddy/example.com
                }

        route /blog* {
                redir /blog /blog/
                reverse_proxy ghost_blog:2368
                }
        }
        
$ docker restart caddy_web_server
```
(replace example.com with your domain)

$ docker run -d --restart=always --name ghost_blog --network master -e url=https://example.com/blog/ -v /home/pi/ghost:/var/lib/ghost/content ghost

Browse [https://example.com/blog/ghost/]