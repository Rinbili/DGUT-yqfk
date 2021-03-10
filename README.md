本Repo仅修改为可自用版本，
## Usage

```
USERNAME   # 学号
PASSWORD   # 中央认证系统密码
SCKEY      # Server 酱密钥
```

[Server 酱密钥获取](http://sc.ftqq.com/)

默认在 00:10 的时候提交

### 方法一 (docker-compose)

```yaml
version: "3.1"

services:
  yqfk:
    image: Rinbili/dgut_yqfk
    environment:
      - USERNAME=
      - PASSWORD=
      - SCKEY=
    restart: always
```

### 方法二 (screen)

可以使用`screen`将程序放置在后台运行(Ctrl + A + D 离开 screen)

```shell script
git clone https://github.com/Rinbili/DGUT-yqfk.git && cd DGUT-yqfk 
pip3 install -r requirements.txt
screen -US yqfk
python3 yqfk.py USERNAME PASSWORD SCKEY
```

