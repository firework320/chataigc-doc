---
layout: home

hero:
  name: 艺创AI
  text: 企业AI解决方案专家
  tagline: 用AI为企业赋能，引领企业实现数字化、智能化转型
  actions:
    - theme: brand
      text: 立即咨询
      link: /contact
      class: 'primary-button'
    
    - theme: alt 
      text: 解决方案
      link: /solutions
      class: 'secondary-button'
    
    - theme: alt
      text: 产品服务
      link: /products
      class: 'secondary-button'
      
    - theme: alt
      text: 帮助文档
      link: /docs
      class: 'secondary-button'

  image:
    src: /images/home/logo.svg
    alt: ChatMoneyAI Logo

features:
  - icon: 💬
    title: AI智聊系统
    details: 快速搭建智能聊天系统，支持公众号、小程序、PC端、APP端全渠道部署
    
  - icon: 🎨
    title: AI绘画系统
    details: 一站式AI绘画解决方案，支持公众号、小程序、抖音小程序等多端接入
    
  - icon: \udd0c
    title: AI接口接入
    details: 为企业微信、钉钉、飞书等办公工具接入AI能力，提升办公效率
    
  - icon: 🧠
    title: 知识库训练
    details: 打造专属企业知识库AI模型，应用于客服、数字人直播等场景
    
  - icon: 💼
    title: 办公赋能
    details: AI辅助PPT制作、表格处理、代码编写，全面提升工作效率
    
  - icon: 🎯
    title: 营销获客
    details: AI客服、文案创作、数据分析，助力企业精准营销

  - icon: 🌐
    title: 多端支持
    details: 支持公众号、H5、小程序、PC端等全渠道部署，数据互通
    
  - icon: ⚡
    title: 快速交付
    details: 5个工作日内完成基础系统搭建，支持企业级定制开发

solutions:
  title: 解决方案
  description: 为不同行业提供专业的AI解决方案
  items:
    - icon: 🏢
      title: 企业服务
      details: 智能客服、知识库管理、办公自动化
      
    - icon: 🏪
      title: 零售电商
      details: 智能导购、个性化推荐、营销获客
      
    - icon: 🏥
      title: 医疗健康
      details: 智能问诊、健康管理、医疗数据分析
      
    - icon: 🎓
      title: 教育培训
      details: AI助教、个性化学习、教学管理
---



## 这里是 AIGC创作系统 文档，采用 VitePress 搭建

在线地址：http://urlnet.cn

启动代码：npm run dev

打包代码：npm run build

Make方式：make dev / make dist

VitePress 说明文档：https://vitepress.vuejs.org/

## 总览

AIGC创作系统 是一个低代码数据可视化开发平台，将图表或页面元素封装为基础组件，无需编写代码即可完成业务需求。
它的技术栈为：
::: info 技术栈

- Vue3 + TypeScript4 + Vite2 + NaiveUI + ECharts5  + Axios + Pinia2 + PlopJS
  :::



 
## 浏览器支持

开发和测试平台均在 Google 和最新版 EDGE 上完成，暂未测试 IE11 等其它浏览器，如有需求请自行测试。

## 安装

本项目采用 pnpm 进行包管理，若要使用其它管理方式，请删除 `pnpm-lock.yaml` 并安装依赖

```shell
#pnpm（建议使用nrm切换到淘宝源）
pnpm install

# npm
npm install

# yarn
yarn install
```

## 启动

```shell
#pnpm
pnpm dev

npm run docs:dev

# npm
npm run dev

#yarn
yarn dev

#Makefile
make dev
```

## 编译

```shell
#pnpm
pnpm run build

# npm
npm run build

#yarn
yarn run build

#Makefile
make dist
```
