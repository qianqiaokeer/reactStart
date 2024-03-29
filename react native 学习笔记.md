# react native 学习笔记
## 环境依赖
+ node

   node版本至少14
+ JDK

   版本至少11
+ Yarn
  
   用于替代npm 提升速度
   ````sh
   npm install -g yarn
   ````
+ Android 环境

   - android studio


+  npm 镜像
   
   一般情况使用淘宝 方便 网络稳定
    ````sh
    npm config set registry http://registry.npmjs.org/
    #淘宝镜像
    npm config set registry https://registry.npm.taobao.org/
    ````
## 项目创建
+ 使用react-native-cli创建项目

   > 老版本卸载 避免一些冲突
   
   ````sh
   npm uninstall -g react-native-cli
   npm install -g react-native-cli
   ````
   > 初始化项目
   
   ````sh
   npx react-native init xxxx
   ````
   xxxx大哥这里表示项目目录

+ 使用create-react-native-app初始化项目

  > 先下载create-react-native-app工具

  ````sh
  npm install -g create-react-native-app
  ````

  > 初始化项目

  ````sh
  create-react-native-app projectName
  cd projectName
  npm install -g expo-cli
  ````

  > 启动项目

  ````sh
  #指定手机连接下载IP地址
  set REACT_NATIVE_PACKAGER_HOSTNAME=192.168.xxx.xxx
  expo start
  ````

## 使用Android设备
+  在Android真机设备上运行应用
   > 开启USB调试 打开usb调试开关
   
   > 使用adb devices 命令检查设备是否正确连接
    ````sh
    adb devices
    ````
   >  运行应用
   ````sh
   npx react-native run-android
   ````
+ Android 模拟器

## 页面导航

> 第三方插件

````sh
yarn add react-navigation
#导航
yarn add react-navigation-stack
#底部导航
yarn add react-navigation-tabs
yarn add react-native-screens
yarn add react-native-reanimated 
yarn add react-native-gesture-handler

yarn add @react-navigation/native
yarn add @react-navigation/native-stack
yarn add @react-navigation/bottom-tabs
````

> swiper

````sh
yarn add react-native-swiper@nighty
````

> Slider滑杆组件

类似调节音量大小的滑杆











nodejs更新很快  搭建项目使用的依赖包版本对nodejs的版本有要求 	nodejs版本低了会发生错误

所以需要去更新nodejs的版本	

可以使用nvm来管理nodejs	可以下载不同版本的nodejs	使用什么版本就切换到什么版本

下载nvm

安装

查看是否安装成功

````sh
nvm version
#查看可用的nodjs版本
nvm ls available
#下载需要的nodejs版本
nvm install xx.xx.x
#使用指定nodejs版本
nvm use xx.xx.x
````




# 问题
> 网速太慢了

+ 换淘宝镜像
   ````sh
   yarn config set registry https://registry.npm.taobao.org
   npm config set registry https://registry.npm.taobao.org
   ````
+ 移除原代理

   ````sh
   yarn config delete proxy
   npm config rm proxy
   ````
+ 查看配置信息

   ````sh
   yarn config list
   ````
> 依赖包冲突
   ````sh
   this command with --force, or --legacy-peer-deps
   Fix the upstream dependency conflict, or retry
   this command with --force, or --legacy-peer-deps
   to accept an incorrect (and potentially broken) dependency resolution.
   ````
+ 解决方案

   ````sh
   npm install --–legacy-peer-deps
   ````
# 非管理员安装MySQL
> 下载zip

> 解压到安装目录

> 到安装目录下创建my.ini文件和data目录 其中my.ini内容如下

````ini
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录
basedir=C:\Users\kehuiz\Myfolder\mysql-8.0.20
# 设置mysql数据库的数据的存放目录
datadir=C:\Users\kehuiz\Myfolder\mysql-8.0.20\data
# 允许最大连接数
max_connections=200
# 允许连接失败的次数。这是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=10
# 服务端使用的字符集默认为UTF8
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用“mysql_native_password”插件认证
default_authentication_plugin=mysql_native_password
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8
[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8
````
> 不是管理员不能install 服务 所以每次使用是去启动MySQL 执行如下代码

````sh
# 启动数据库
mysqld --console
````

````sh
# 修改密码
mysqld --console --skip-grant-tables --shared-memory
````
> 修改密码
````sql
update user set host = '%' where host = 'localhost' and user = 'root';
flush privileges;
alter user 'root'@'%' identified with mysql_native_password by '123456';
flush privileges;
--ip 指定 可能有多个mysql
mysql -u root -h 192.168.194.142 -p
-- mysql8给用户eladmin赋权
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, RELOAD, INDEX, 
ALTER,CREATE VIEW, SHOW VIEW,  EVENT, TRIGGER, CREATE TABLESPACE
ON *.* TO `eladmin`@`%` ;
````


````sh
info yarn config
{
  'version-tag-prefix': 'v',
  'version-git-tag': true,
  'version-commit-hooks': true,
  'version-git-sign': false,
  'version-git-message': 'v%s',
  'init-version': '1.0.0',
  'init-license': 'MIT',
  'save-prefix': '^',
  'bin-links': true,
  'ignore-scripts': false,
  'ignore-optional': false,
  registry: 'https://registry.yarnpkg.com',
  'strict-ssl': true,
  'user-agent': 'yarn/1.22.19 npm/? node/v15.5.1 win32 x64'
}
info npm config
{
  registry: 'http://registry.npmjs.org/',
  home: 'https://npm.taobao.org',
  prefix: 'C:\\Users\\kehuiz\\Myfolder\\node-v16.15.1-win-x64\\node_global',
  cache: 'C:\\Users\\kehuiz\\Myfolder\\node-v16.15.1-win-x64\\node_cache',
  proxy: 'http://165.225.216.25:10077/'
}
````

````sh
 ERROR  Error: Element type is invalid: expected a string (for built-in components) or a class/function (for composite components) but got: undefined. You likely forgot to export your component from the file it's defined in, or you might have mixed up default and named imports.
````

详细查找你导入的js文件，定义的字符串或函数名称引用错误

````js
import Slider from '@react-native-community/slider';
````

