# Capistrano Template

This is an example template to illustrate the book https://leanpub.com/railsbuntu

Template to deploy simple HTML site with Capistrano

  -1) Clone this project:

  -2) then assuming you have rbenv already installed with ruby 2.5.0

```
bundle install
```

 -3) Moved your html file in the `www` folder 


 -4) On the server (linux server) create a user called `deployer`
 
allow ssh with user deployer


  -5) Update config/deploy/production.rb by adding your real IP:

```bash
role :web,%w{deployer@REPLACE_WITH_SERVER_IP}
``` 


 -6) Change Nginx (or apache ) configuration:

Example here with nginx
```
server {
                listen       80;
                server_name  www.myurl.co.uk;

                location / {
                    root   /home/deployer/my_web_site/current/www;
                    index  index.html;
                } 
}

```

 -7) Then once ready:
  
```bash
bundle exec cap production deploy
```