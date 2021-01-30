# easydarwin
视频rtsp拉取分发
# EasyDarwin开源流媒体服务器


- 直接运行(Linux)

		cd EasyDarwin
		./easydarwin
		# Ctrl + C

- 以服务启动(Linux)

		cd EasyDarwin
		./start.sh
		# ./stop.sh

- 查看界面
	
	打开浏览器输入 [http://localhost:10008](http://localhost:10008), 进入控制页面,默认用户名密码是admin/admin

- 测试推流

	ffmpeg -re -i C:\Users\Administrator\Videos\test.mkv -rtsp_transport tcp -vcodec h264 -f rtsp rtsp://localhost/test

	ffmpeg -re -i C:\Users\Administrator\Videos\test.mkv -rtsp_transport udp -vcodec h264 -f rtsp rtsp://localhost/test
			

- 测试播放

	ffplay -rtsp_transport tcp rtsp://localhost/test

	ffplay rtsp://localhost/test 


## 手机推流

可以使用EasyPusher测试手机推流,[下载地址](https://github.com/EasyDSS/EasyPusher)

推流URL规则: rtsp://{ip}:{port}/{id} ， 例如 : rtsp://www.easydarwin.org:554/your_stream_id

EasyPusher参数设置如下

![snapshot](http://ww1.sinaimg.cn/large/79414a05ly1fwzqe8oyjxj20u01hcafw.jpg)

可使用vlc播放器、[EasyScreenLive](https://github.com/EasyDSS/EasyScreenLive)、[EasyPlayer-RTSP](https://github.com/EasyDSS/EasyPlayer-RTSP-Win/releases)、[EasyPlayerPro](https://github.com/EasyDSS/EasyPlayerPro-Win)测试播放

## 效果图

![snapshot](http://ww1.sinaimg.cn/large/79414a05ly1fwzqdbi8efj20w00mrn0c.jpg)

## 二次开发

### 准备工具

- node 系

        npm i -g rimraf
        npm i -g @epcom/pack

- go 系

        go get -u github.com/kardianos/govendor
        go get -u github.com/caixw/gobuild

### 编译命令

-
- 以开发模式运行 server

        npm run dev

- 以开发模式运行前端

        npm run dev:www       

- 编译前端

        cd web_src && npm i
        cd ..
        npm run build:www

- 编译 Windows 版本

        npm run build:win

- 编译 Linux 版本 (在 bash 环境下执行)

        npm run build:lin       

- 清理编译文件

        npm run clean 

- 打包

        # for windows
        npm run build:win
        pack zip

        # for linux 
        npm run build:lin
        pack tar

        # for clean
        pack clean

