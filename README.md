本Repo为自用版本，不保证脚本能正常运行
## Usage

```
USERNAME   # 学号
PASSWORD   # 中央认证系统密码
SCKEY      # Server 酱密钥
```

[Server 酱密钥获取](http://sct.ftqq.com/)


### 使用 (Actions) 
1、Fork本项目
2、启用workflow
3、在Settings>>Secrect 添加USERNAME,USERPASSWD,SCKEY三个Actions secrets(不想使用Server 酱的话SCKEY填None)
4、每两个月重新激活一次
workflows：（仅供参考）

```shell script
name: DGUT_yqfk

on:
    workflow_dispatch:
    schedule:
        - cron: "15 16,17,18  *  *  *"
    watch:
        types: [started]


jobs:
  build:
    runs-on: ubuntu-latest
    steps:
            - name: Checkout
              uses: actions/checkout@v2
        
            - name: "Set up Python"
              uses: actions/setup-python@v1
              with:
                python-version: 3.8

            - name: "requirements"
              run: pip3 install -r requirements.txt

            - name: "Run yqfk"
              env:
                USERNAME: ${{ secrets.USERNAME }}
                PASSWORD: ${{ secrets.USERPASSWD }}
                SCKEY: ${{ secrets.SCKEY }}
              run: 
                python yqfk.py
```
