# 🚨 常见错误问题处理

## 🔑 授权错误提示

### 1. 站点设置多域名
- **问题描述**：站点配置了两个域名，但授权文件只支持单域名
- **解决方案**：删除未授权的域名即可

### 2. 反向代理和Docker运行
- **问题描述**：使用反向代理导致授权文件无法识别
- **解决方案**：
  1. 发送域名选项填写`$host`
  2. 如果是Docker反向代理，需将Docker域名设置为与授权域名一致
  3. 修改后：
     - Nginx：重启Nginx服务
     - Docker：重启容器
- **参考截图**：
  ![授权错误1](https://doc.chatmoney.cn/docs/images/general/qa/error/license-3-1.png)
  ![授权错误2](https://doc.chatmoney.cn/docs/images/general/qa/error/license-3-2.png)

## 💻 PC端无法扫码登录

### 1. 缺少配置
- **配置步骤**：
  1. 登录管理后台 -> 【渠道设置】 -> 【微信公众号设置】 -> 【公众号配置】
  2. 登录[微信公众平台](https://mp.weixin.qq.com/)
  3. 进入【设置与开发】 -> 【基本设置】
  4. 按提示填写相关信息
- **参考截图**：
  ![PC端微信登录](https://doc.chatmoney.cn/docs/images/general/qa/error/pc-wechat-login.png)

### 2. 域名被封禁
- **问题描述**：域名被微信封禁导致无法扫码登录
- **解决方案**：
  1. 通过微信发送链接测试
  2. 如确认被封，可进行申诉

## 💳 微信支付问题

### 1. API密钥配置错误
- **问题描述**：未正确配置API3密钥
- **解决方案**：
  - 必须使用API3密钥，而非API2密钥
  - API2密钥会导致支付回调异常

### 2. API密钥重复
- **问题描述**：API2和API3密钥设置相同
- **解决方案**：确保API2和API3密钥不同

### 3. 证书配置错误
- **问题描述**：微信支付证书和密钥配置颠倒
- **解决方案**：正确区分支付证书和密钥

## 🖼️ 海报生成问题
- **解决方案**：更新系统后重新选择图片设置海报背景

## 📱 小程序问题

### 1. 编译错误
- **解决方案**：
  1. 重新下载最新源码
  2. 删除依赖后重新编译
- **参考截图**：
  ![小程序编译错误](https://doc.chatmoney.cn/docs/images/general/qa/error/mnp-build.png)

### 2. 图片下载失败
- **错误提示**：`downloadFile:fail ur not in domain list`
- **解决方案**：
  1. 获取图片域名：
     - 进入后台【绘画记录】
     - 右键图片获取域名
  2. 在小程序后台添加该域名
- **参考截图**：
  ![下载错误](https://doc.chatmoney.cn/docs/images/general/qa/error/mnp-download-error.png)
  ![获取域名](https://doc.chatmoney.cn/docs/images/general/qa/error/mnp-download-url.png)

## 🎨 MJ绘图问题

### 1. 官网绘图失败
- **排查步骤**：
  1. 登录MJ账号确认绘图状态
  2. 检查提示词是否正确

### 2. 代理域名错误
- **排查要点**：
  - 检查图片代理域名配置
  - 确保使用HTTPS协议
  - 检查防火墙设置

### 3. 文档阅读不完整
- **建议**：仔细阅读全部文档内容

## 🚦 502错误
- **问题原因**：PHP扩展冲突
- **解决方案**：
  1. 检查所有PHP版本
  2. 移除opcache扩展
- **参考截图**：
  ![502错误](https://doc.chatmoney.cn/docs/images/general/php/error/502-1.png)

## 🔐 忘记管理员密码
- **重置步骤**：
  1. 登录宝塔面板
  2. 进入【网站】 -> 【PHP项目】
  3. 找到对应站点，进入根目录
  4. 打开终端
  5. 执行命令：`php think password 新密码`
- **参考截图**：
  ![密码重置1](https://doc.chatmoney.cn/docs/images/general/php/error/password-1.png)
  ![密码重置2](https://doc.chatmoney.cn/docs/images/general/php/error/password-2.png)
  ![密码重置3](https://doc.chatmoney.cn/docs/images/general/php/error/password-3.png)

## ⚠️ 500错误
- **处理方式**：请参考专门的500错误文档