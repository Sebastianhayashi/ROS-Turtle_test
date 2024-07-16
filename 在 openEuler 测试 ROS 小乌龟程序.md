## 启动虚拟机

使用 PROXMOX 启动虚拟机，并且进入 openEuler 安装程序。

![[proxmox-boot.png]]
## openEuler 安装

在进入 openEuler 的安装界面后，创建用户与 root 用户，以及选择安装位置即可进行安装。
![[install.png]]

![[configuration.png]]

以下是 openEuler 安装过程图：

![[installation.png]]

### 预期行为：

安装成功。

#### 实际行为：

安装成功（如下图）。
![[complete-installation.png]]

进入系统后使用 `./neofetch` 输出系统信息：

![[install-succeed.png]]
### 其他说明

我使用他人提的服务器开启虚拟机，所以需要 root 管理员创建虚拟机，我无法提供创建虚拟机的过程，所以只有提供安装 openEuler 的过程。

## 安装 ROS

根据[教程](https://gitee.com/openeuler/ros/tree/master/user_doc/ROS-humble-oerv24.03-x86#/openeuler/ros/blob/master/user_doc/ROS-humble-oerv24.03-x86/logs/dnf_install.log)进行 ROS 测试安装：
- 执行如下命令进行对软件源的修改：
```log
bash -c 'cat << EOF > /etc/yum.repos.d/ROS.repo
[openEulerROS-humble]
name=openEulerROS-humble
baseurl=http://121.36.84.172/dailybuild/EBS-openEuler-24.03-LTS/EBS-openEuler-24.03-LTS/EPOL/multi_version/ROS/humble/x86_64/
enabled=1
gpgcheck=0
EOF'
```

> 修改时发现需要使用 `sudo`

- 开始安装包，执行如下指令：
`dnf install "ros-humble-*" --skip-broken --exclude=ros-humble-generate-parameter-library-example`

> 安装时发现需要使用 sudo

执行以下指令：

`source /opt/ros/humble/setup.sh`

`source ~/.bashrc`

### 遇到的问题

![[turtle-issue.png]]

小乌龟窗口可以正常显示，但是无法进行移动。