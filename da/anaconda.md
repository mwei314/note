## 安装
直接用 `sudo pacman -S anaconda`，然后用`conda -h`测试结果没有找到命令
安装完成之后有下面的提示：
Please run
	$ source /opt/anaconda/bin/activate root
	$ source /opt/anaconda/bin/deactivate root
to activate and deactivate the anaconda enviroment.

在～/.bashrc中配置环境变量
```
#anaconda
export PATH=$PATH:/opt/anaconda/bin
```
然后`source .bashrc`解决问题

## 源
参考https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/，先`conda config --set show_channel_urls yes`生成配置文件'~/.condarc'，改成
```
channels:
  - defaults
show_channel_urls: true
channel_alias: https://mirrors.tuna.tsinghua.edu.cn/anaconda
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/pro
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
```