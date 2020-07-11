# fake115uploader
模拟115网盘客户端的上传功能，部分实现参考 [Fake115Upload](https://github.com/T3rry7f/Fake115Upload)

### 特点
* 支持秒传模式，需要已经有人上传过指定文件到115
* 支持上传超大文件，超过5G的文件需要115 vip会员
* 支持断点续传（实验性质）
* 支持显示上传进度条

### 安装
`go get -u github.com/orzogc/fake115uploader`

### 使用方法
首先要先运行一次 `fake115uploader` 生成设置文件config.json，然后登陆网页版115，按F12后刷新，将115网页请求的Cookie的值全部复制到config.json的cookies的值里

`fake115uploader -f 文件` 秒传模式上传文件

`fake115uploader -u 文件` 先尝试用秒传模式上传文件，失败后改用普通模式上传

`fake115uploader -m 文件` 先尝试用秒传模式上传文件，失败后改用断点续传模式上传，可以随时中断下载再重启下载（实验性质，请谨慎使用，注意断点时间不要过长）

要上传文件到指定的115文件夹，可以在config.json或运行时加上参数 `-c cid` 设置cid（参数设置会覆盖设置文件里的设置，默认为0，即根目录），cid为115文件夹的cid，可以登陆115网页版查看网页地址获取cid

运行时加上参数 `-v` 显示更详细的信息（调试用）
