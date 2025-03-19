# LF Server Info Documentation
> LFNL 基础服务器 SSD1306 小屏幕的信息显示

## 测试 | 使用方法
- make
- sudo ./LFDevInfo

## 如何开机自启

### 目标
- 服务位置：系统级目录 /etc/systemd/system/。
- 运行用户：以某个用户（如 orangepi 或 root）运行服务，但所有用户都能通过某种方式调用或访问程序。
- 启动时机：系统启动时自动运行。
- 权限开放：所有用户都可以执行 /usr/local/bin/LFDevInfo。
  
### 命令
1. make
2. sudo mv ./LFDevInfo /usr/local/bin/
3. sudo chmod 755 /usr/local/bin/LFDevInfo
4. sudo nano /etc/systemd/system/lfdevinfo.service
<br>

#### 输入以下内容
> [Unit]
> Description=LFDevInfo System Monitor for orangepi
> After=network.target
> 
> [Service]
> ExecStart=/usr/local/bin/LFDevInfo
> Restart=always
> User=root
> 
> [Install]
> WantedBy=default.target

### 命令
1. sudo chmod 644 /etc/systemd/system/lfdevinfo.service
2. sudo systemctl daemon-reload
3. sudo systemctl enable lfdevinfo.service
4. sudo systemctl start lfdevinfo.service
5. sudo systemctl status lfdevinfo.service

### 测试
- sudo reboot
- sudo systemctl status lfdevinfo.service

## 后记
代码来源于Temperature6作者
<br>
源仓库：https://github.com/Temperature6/OPi4_RTDevInfo/tree/main
<br>
侵删
