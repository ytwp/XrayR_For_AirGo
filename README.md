# XrayR_For_AirGo

### 1.直接安装 XrayR

```
bash <(curl -Ls https://raw.githubusercontent.com/AirGo-Official/XrayR_For_AirGo/main/scripts/manage.sh)
```

- 安装完成后请根据需要在```/usr/local/XrayR/config.yml```中修改配置文件
- 启动：使用管理脚本```XrayR```或直接 `systemctl start XrayR`

### 2.docker 安装 XrayR

- 提前准备好配置文件 config.yml，参考 [config.yml](https://github.com/AirGo-Official/XrayR_For_AirGo/blob/main/config.yml)

- 启动docker命令参考如下：

```
docker run -tid \
  -v $PWD/xrayr/config.yml:/etc/XrayR/config.yml \
  --name xrayr \
  --restart always \
  --net=host \
  --privileged=true \
  ppoiuty/xrayr:latest
```

- docker compose参考如下：

```
version: '3'
services:
  xrayr:
    container_name: xrayr
    image: ppoiuty/xrayr:latest
    network_mode: "host"
    restart: "always"
    privileged: true
    volumes:
      - ./config.yml:/etc/XrayR/config.yml
```
