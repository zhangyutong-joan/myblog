+++
date = '2025-07-27T01:17:13+08:00'
draft = false
title = '一些常用命令'
tags = ["linux", "git", "conda"]
categories = ["开发日志"]

image = "https://s.panlai.com/upload/bizhihui_com_20231109221056169953905656676.png-arthumbs"
+++

## linux命令
```
wget https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh --no-check-certificate # 安装anaconda
useradd -m 用户名 # 创建用户
passwd 用户名 # 设密码
su zyt # 登录
source ~/.bashrc # 更新配置文件
du -h -x --max-depth=1 # 查看当前文件夹下的各个文件夹所占内存
df -h #显示文件系统的磁盘空间使用情况
sudo shutdown -r now # 重启远程 Linux 主机

chown -R liuhai:liuhai /opt # 将目录/opt 及其下面的所有文件、子目录的文件主改成 liuhai

gpustat -i # 实时监视GPU使用情况(删去-i就不实时)
```
vim:按ESC键 跳到命令模式，然后输入:q（不保存）或者:wq（保存） 退出。

node.js启动:
nvm use 22.16.0
rm ..
npm install
npm run dev


## conda命令
```
conda update -n base conda #update最新版本的conda
conda activate xxxx #开启xxxx环境
conda deactivate  #关闭环境
conda remove -n xxxx --all  #删除xxxx环境
conda env list #显示所有的虚拟环境
conda info --envs #显示所有的虚拟环境

conda create --name xxxx python=xxxx #创建新的虚拟环境

conda list         #查看已经安装的文件包
conda list -n xxxx       #指定查看xxxx虚拟环境下安装的package
conda update xxxx   #更新xxxx文件包
conda uninstall xxxx   #卸载xxxx文件包
```

## mamba
```
mamba info --envs # 查看mamba下所有环境

mamba create -n py_310 python=3.10 # 创建新环境: -n 自定义名称 python=版本号
mamba create -n dl_env python=3.11 pytorch=2.3.1 tensorflow=2.15 -c conda-forge # 创建新环境并拉取多个库
mamba create --clone py_310 --name new_py_310 # 克隆环境

mamba remove -n py_310 --all # 删除环境
mamba activate py_310 # 激活环境 py_310是刚才新创建的环境名
mamba deactivate # 退出环境

mamba install xxx # 安装库包，多个包
mamba remove numpy # 删除库包
mamba update numpy # 更新库包
mamba update --all # 更新所有库包
mamba clean --all -y # 清理所有缓存
```

## git命令
```
git remote -v # 查看远程仓库别名
git add <file name> # 将文件放到暂存区
git commit -m "注释" # 将暂存区提交到本地仓库
git push <仓库别名> # 将本地仓库推送到远程仓库
git pull <仓库别名> # 将远程仓库拉取到本地仓库
```
其他的：
```
git remote add origin https://github.com/zyt1998/xxx.git # 添加远程仓库
git remote rm origin # 删除远程仓库
git push -u origin master # 将本地仓库推送到远程仓库
git pull origin master # 将远程仓库拉取到本地仓库
git clone https://github.com/zyt1998/xxx.git # 克隆远程仓库
git add . # 将所有文件添加到暂存区
git commit -m "xxx" # 将暂存区提交到本地仓库
git push origin master # 将本地仓库推送到远程仓库
git branch # 显示你的仓库的所有本地分支，星号分支是您当前的分支。

git rm --cached 文件 //本地中该文件不会被删除
git rm -r  --cached  文件夹 //删除文件夹
```
fork了别人的项目之后如何保持同步更新
```
git fetch upstream # 胡拉取远程仓库的更新
git checkout main # 切换到master分支
git merge upstream/main # 合并远程仓库的更新到本地仓库
git push origin main # 将本地仓库的更新推送到远程fork的仓库
```
博客更新后怎么push：
```
# 根目录下，保存配置改动
git add config.yaml
git commit -m "更新配置文件"
git push origin main

# 重新生成静态文件
hugo

# 推送 public/ 到 main
cd public
git add .
git commit -m "更新部署内容"
git push origin main
cd ..
```

push时网络问题
```
# 设置系统代理
git config --global http.proxy http://127.0.0.1:xxxx # 梯子在xxxx端口号就是这个
git config --global https.proxy http://127.0.0.1:xxxx
```

## matlab
```
ylim([-2 2]) % 画图，y轴范围

```
## vscode一些设置
word warp：自动换行

## 其他
- sklearn全称为**scikit-learn**
- windows cmd 切换到d盘:  ```cd /d D:```
- 开启jupyter直接在终端输入```jupyter notebook --allow-root```然后复制terminal下的“Jupyter Notebook 6.3.0 is running at:”下面的链接到浏览器就可以了。

```
nvidia-smi  #查看gpu是否空闲
nvidia-smi -L  #查看gpu型号
torch.cuda.is_available()  #查看gpu是否可用
torch.cuda.device_count()  #查看gpu可用数量
```

将服务器端的文件或文件夹下载到本地:
- 下载文件：```scp root@【服务器的IP地址】:/home/zyt/.../【原文件名】 【本地路径】/【目标文件名】```
- 下载文件夹：```scp -r root@【服务器的IP地址】:/home/zyt/... 【本地路径】```

```pip show xxx```查看包的版本等信息

python项目中导出requirements.txt(不含有文件路径)：```pip list --format=freeze > requirements.txt ```

对于MySQL是否开机自启，建议手动启动，需要时Win + R 打开“运行”对话框，输入services.msc，点击确定或直接Enter键，进入"服务"管理器窗口，找到MySQL，右键“启动”就好。



[PyTorch中torch、torchvision、torchaudio、torchtext版本对应关系](https://blog.csdn.net/shiwanghualuo/article/details/122860521)

[pytorch与cuda版本对应关系汇总](https://gitcode.csdn.net/65e9388c1a836825ed78dcca.html?dp_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MzM3NDQyOSwiZXhwIjoxNzE4MTgyMTE4LCJpYXQiOjE3MTc1NzczMTgsInVzZXJuYW1lIjoibTBfNDY1MTg2NTYifQ.rGCPZ_4XU6UkI1Dmo1h7v6OmLtbw3NQfbkAiW8OYYzc)

[【CUDA】GPU 算力与 CUDA 版本对应关系](https://blog.csdn.net/weixin_43667077/article/details/135654738)


[一篇文章教你清理 Anaconda 的 pkgs](https://blog.csdn.net/Robin_Pi/article/details/115004870)

os.walk用法：
```
def walkFile(file):
    for root, dirs, files in os.walk(file):

        # root 表示当前正在访问的文件夹路径
        # dirs 表示该文件夹下的子目录名list
        # files 表示该文件夹下的文件list

        # 遍历文件
        for f in files:
            print(os.path.join(root, f))

        # 遍历所有的文件夹
        for d in dirs:
            print(os.path.join(root, d))
```

获取脚本所在目录
```
os.path.split(os.path.realpath(__file__))[0]
```
