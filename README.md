##TODO
eslint
babel
jest
---

##Github Url:
**[github url](https://github.com/Aggie123/fullstack-startkit)**

---

##Project Framework:
	- front-end: React + React Router + Antd + Redux + Axios
	- back-end: MongoDB + Node + Express

---

##How to clone this project:

```
	1. git clone git@github.com:Aggie123/fullstack-startkit.git
	2. git submodule init
	3. git submodule update
	4. npm install
	5. cd fullstack-frontend&&npm install
	6. cd fullstack-backend&&npm install

```
---

##How to start this project:
`npm start`

##How to build this project:


##How to config dev env:
1. config hosts:
    vim /etc/hosts
    `127.0.0.1 home.sunshine.com`

2. config nginx sever:
    vim /usr/local/etc/nginx/nginx.conf
    (nginx -s reload)
    ```
    server {
        listen       80;
        server_name  home.sunshine.com;

        #frontend route
        location / {
              root   html;
              index  index.html index.htm index.js;
              #proxy_set_header   X-Real-IP        $remote_addr;
              #proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
              #proxy_set_header   Host             $http_host;
              #proxy_set_header   X-NginX-Proxy    true;
              proxy_set_header   Connection "";
              proxy_http_version 1.1;
              proxy_pass http://127.0.0.1:3000;
        }
        #backend route
        location /api {
              proxy_set_header   X-Real-IP        $remote_addr;
              proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
              proxy_set_header   X-NginX-Proxy    true;
              proxy_set_header   Connection "";
              proxy_set_header   Host             $http_host;
              proxy_http_version 1.1;
              proxy_pass http://127.0.0.1:3001;
        }
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }
  }
  ```