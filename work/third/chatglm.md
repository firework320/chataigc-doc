# 🤖 ChatGLM本地模型部署

## 🚀 ChatGLM2-6B

### 📖 ChatGLM2-6B 简介

ChatGLM2-6B 是开源中英双语对话模型 ChatGLM-6B 的第二代版本，具体介绍可参阅 [ChatGLM2-6B 项目主页](https://github.com/THUDM/ChatGLM2-6B)

::: warning ⚠️ 注意
ChatGLM2-6B 权重对学术研究完全开放，在获得官方的书面许可后，亦允许商业使用。本教程只是介绍了一种用法，无权给予任何授权！
:::

### 💻 推荐配置

依据官方数据，同样是生成 8192 长度，量化等级为 FP16 要占用 12.8GB 显存、int8 为 8.1GB 显存、int4 为 5.1GB 显存，量化后会稍微影响性能，但不多。

| 类型 | 内存           | 显存           | 硬盘空间       |
| ------ | ---------------- | ---------------- | ---------------- |
| fp16 | \>\=16GB | \>\=16GB | \>\=25GB |
| int8 | \>\=16GB | \>\=9GB  | \>\=25GB |
| int4 | \>\=16GB | \>\=6GB  | \>\=25GB |

### 🛠️ 源码部署

::: tip 💡 提示
根据上面的环境配置配置好环境，具体教程自行百度；
可参考的部署文章: [https://blog.csdn.net/lovelylord/article/details/132349967](https://blog.csdn.net/lovelylord/article/details/132349967)
:::

* **1️⃣ 从GitHub仓库中拉取代码**

```bash
# 1.从GitHub仓库中拉取代码
git clone https://github.com/THUDM/ChatGLM2-6B

# 2.进入下载源码的目录
cd ChatGLM2-6B
```

* **2️⃣ 下载python文件：**  [📥 点击下载Python文件](https://doc.chatmoney.cn/docs/download/glm.zip)

    * 得到两个文件: openai_ai.py 和 requirements.txt
    * 把这两个文件替换到 ChatGLM2-6B 目录里面
* **3️⃣ 安装依赖：**  **​`pip install -r requirments.txt`​**

    * 建议使用python的虚拟环境,以免产生一些不必要的麻烦。
* **4️⃣ 运行项目：**  **​`python openai_api.py --model 16`​** **这里的数字根据上面的配置进行选择。**

    * 然后等待模型下载，直到模型加载完毕为止。如果出现报错先问百度。
    * 这里可能需要科学上网
* **5️⃣ 启动成功后应该会显示如下地址：**

::: tip 💡 提示
这里的 [http://0.0.0.0:8000](http://0.0.0.0:8000/) 就是连接地址。
:::

![启动界面](https://doc.chatmoney.cn/docs/images/general/third-deployment/chat-glm/chatglm-start.png)

### ⚙️ 关于 openai_api.py 启动参数

| 参数名   | 可选值                                                             | 默认值 |
| ---------- | -------------------------------------------------------------------- | -------- |
| --device | cuda\=显卡运行, cpu\=cpu运行                                 | cuda   |
| --path   | local\=本地下载的模型运行, thudm\=线上自动下载               | thudm  |
| --model  | 4\=chatglm2-6b-int4, 8\=chatglm2-6b-int8, 16\=chatglm2-6b | 16     |

* 📝 说明:
    * 如果你 `--path` 参数设置为 local, 那需要你先把模型下载下来, 放到 ChatGLM2-6B/models 目录下
    * 比如: ChatGLM2-6B/models/chatglm2-6b-int4
    * 然后再去运行: `python openai_api.py --model 4 --path local`

### 🧪 接口测试

![接口测试](https://doc.chatmoney.cn/docs/images/general/third-deployment/chat-glm/chatglm-post.png)

### 🔗 接入到系统

![系统接入](https://doc.chatmoney.cn/docs/images/general/third-deployment/chat-glm/chatglm-set.png)

## 🚀 ChatGLM3-6B

::: warning ⚠️ 注意
部署方案和ChatGLM2-6B的方式基本上是一样的。
:::

* **1️⃣ 从GitHub仓库中拉取代码**

```bash
# 1.从GitHub仓库中拉取代码
https://github.com/THUDM/ChatGLM3

# 2.进入下载源码的目录
cd ChatGLM3-6B
```

// ... 中间部分保持不变 ...

* **8️⃣ 关于 openai_api.py 启动参数**

| 参数名   | 可选值                                                                              | 默认值 |
| ---------- | ------------------------------------------------------------------------------------- | -------- |
| --device | cuda\=显卡运行, cpu\=cpu运行                                                  | cuda   |
| --path   | local\=本地下载的模型运行, thudm\=线上自动下载                                | thudm  |
| --model  | 4\=量化模型, 16\=chatglm3-6b, 32\=chatglm2-6b-32k, 128\=chatglm2-6b-32k | 4      |

* 📝 说明:
    * 如果你 `--path` 参数设置为 local, 那需要你先把模型下载下来, 放到 ChatGLM2-6B/models 目录下
    * 比如: ChatGLM3-6B/models/chatglm3-6b
    * 然后再去运行: `python openai_api.py --model 4 --path local`
    * 💡 温馨小提示：GLM3不再像之前GLM2那样单独提供量化版本模型下载，现在是量化模型直接继承在 chatglm3-6b模型上，使用运行命令作为区分。