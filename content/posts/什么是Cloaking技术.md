+++
date = '2025-05-25T13:15:19+08:00'
draft = false
title = '什么是Cloaking技术'
+++

### 📌 定义：

**Cloaking（隐形门页）是指向搜索引擎和用户展示不同的页面内容**。

### 📌 实现方式：

通过识别 User-Agent 或 IP 来判断访问者是“搜索引擎蜘蛛”还是“真实用户”，然后：

- 向蜘蛛展示关键词堆砌的 SEO 页面；
- 向用户展示正常页面或跳转到商业站。

### 👨‍💻 技术手段：

- `if($_SERVER['HTTP_USER_AGENT'] == 'Baiduspider') { ... }`
- IP 黑名单/白名单；
- UA、Referer、Cookie 判断。

### 🔍 检测方式：

- 模拟蜘蛛访问页面（设置 User-Agent 为 Baiduspider、Googlebot）；
- 与普通浏览器访问内容对比。

### ⚠️ 风险：

Google、百度明令禁止 cloaking，属于重大违规行为，被抓即 K 站（移除索引）。