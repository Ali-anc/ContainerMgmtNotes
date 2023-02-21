# Few Docker flags information

> ### -p internalport(how its access):serviceport(what it's used for, app service port on container  # <Host Port>:<Container Port>
> ### -v internalpath(where it's mapped internally on the server):servicepath(where it's path on the container). #This is called a bind mount 
> ### you can also create volume by issuing, "docker volume create VOLUMENAME" and then map it for environment exmaple below
  
  
```
 -v <source>:<destination>:<options>
```
```
docker volume create devolrs
```
 
> ### If a volume is completely empty, the container’s content is copied to the volume
```
-v devolrs:/usr/share/nginx/html nginx  
```

 ```
docker run -d --restart=always -p <YOUR_PORT>:3001 -v <YOUR_DIR OR VOLUME>:/app/data --name uptime-kuma louislam/uptime-kuma:1
 ``` 
