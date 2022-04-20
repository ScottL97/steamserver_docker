# steamserver_docker
dockerfiles of steam game servers

## dst

* 饥荒服务器dockerfile
* 挂载目录：

```shell
/home/steam/dst/servers:/root/.klei/DoNotStarveTogether # 存档
/home/steam/dst/mods:/home/steam/dontstarvetogether_dedicated_server/mods # mods
```

* 容器启动命令：

```shell
docker run -itd -p 10999-11000:10999-11000/udp -p 12346-12347:12346-12347/udp -v /home/steam/dst/servers:/root/.klei/DoNotStarveTogether -v /home/steam/dst/mods:/home/steam/dontstarvetogether_dedicated_server/mods dst:v1.1
```
