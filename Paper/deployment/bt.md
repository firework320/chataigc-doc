# 宝塔面板部署指南 - 推荐使用①/③

## 📋 环境要求

> **推荐服务器最低配置**：
> - CPU：双核
> - 内存：4GB
> - 硬盘：20GB
> - 带宽：5兆

**💡 强烈推荐在正式环境中使用宝塔面板部署项目，让部署更加便捷，减少问题发生。**

## 🛠️ 服务器环境设置

### **步骤1**: 安装基础运行环境

点击【软件商店】→【运行环境】，安装以下软件：
- Nginx
- MySQL (5.7版本)
- PHP-8.0
- Redis

⚠️ **警告**
> 安装软件时，请使用极速安装，必须使用PHP8.0和MySQL5.7，否则将无法正常使用。

![基础环境安装-1](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-env-1.png)  
![基础环境安装-2](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-env-2.png)  

### **步骤2**: 安装PHP扩展

点击【软件商店】→【已安装】，找到PHP-8.0，然后点击【设置】→【安装扩展】，安装以下扩展：
- fileinfo扩展
- redis扩展

![PHP扩展安装](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-env-3.png)  

## 🌐 站点部署

### **步骤1**: 上传并解压项目文件

打开宝塔面板，进入`/www/wwwroot`目录，上传下载好的压缩包并解压，解压出来的文件夹即为项目目录。

⚠️ **警告**
> 请确保项目目录及子目录用户设置为www！如果后续步骤出现问题，请重新设置项目目录及子目录用户为www。

![上传项目文件](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-1-1.png)  
![解压项目文件](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-1-2.png)  

### **步骤2**: 添加网站

点击【网站】→【PHP项目】→【添加站点】，按以下信息填写：
- 【域名】：填写已解析到本服务器的域名
- 【根目录】：选择上一步解压好的项目目录中的server目录
- 【数据库】：选择【MySQL】
- 【数据库账号】：设置账号密码
- 【PHP版本】：选择【PHP-80】
- 点击【提交】

⚠️ **警告**
> 站点目录必须选择server，请勿选择public！选择public会导致宝塔生成配置错误，后续修改也无法解决，只能删除站点重新添加。

![添加网站](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-2.png)  

### **步骤3**: 记录数据库信息

请妥善保存数据库名、用户名和密码，步骤13将会用到这些信息。

![保存数据库信息](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-3.png)  

### **步骤4**: 申请SSL证书

找到网站，点击【设置】→【SSL】→【Let's Encrypt】→【文件验证】→【选择域名】→【申请】，完成SSL证书申请。

![SSL证书申请-1](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-4-1.png)  
![SSL证书申请-2](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-4-2.png)  

### **步骤5**: 设置网站目录

点击【网站目录】→【网站目录】，选择解压的项目目录下的"server"目录，点击保存。
然后设置【运行目录】为"/public"，点击【保存】。

![设置网站目录](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-5.png)  

### **步骤6**: 配置伪静态

点击【伪静态】，选择【thinkphp】，点击【保存】。

![配置伪静态](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-6.png)  

## 📦 程序安装

### **步骤7**: 启动安装向导

访问设置的网站，进入程序安装界面，点击【我已阅读同意】。

![安装向导-1](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-7-1.png)  
![安装向导-2](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-7-2.png)  

### **步骤8**: 环境检测

系统将对环境进行检测，通常除了【swoole_loader扩展】外，其他项都会通过。
请注意说明内容中是否提示【非线程安全扩展】或【线程安全扩展】，记住这个信息，步骤9、10、11将用到。

![环境检测](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-8.png)  

### **步骤9**: 复制扩展文件

打开宝塔文件管理，进入项目所在的`/server/license`目录：
- 如果步骤8提示【非线程安全扩展】，复制`swoole_loader80.so`文件
- 如果提示【线程安全扩展】，复制`swoole_loader80_zts.so`文件

![复制扩展文件](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-9.png)  

### **步骤10**: 粘贴扩展文件

打开宝塔文件管理，进入`/www/server/php/80/lib/php/extensions/no-debug-non-zts-20200930`目录，
粘贴文件，并统一改名为`swoole_loader80.so`。

![粘贴扩展文件](https://doc.mddai.cn/docs/images/cp/deployment/bt/bt-10.png)  

### **步骤11**: 配置PHP加载扩展

打开【软件商店】→【运行环境】→【设置】→【配置文件】，在末尾添加：
