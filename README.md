# 腾讯 ima 知识库 · Tencent IMA Skills

> ima 笔记与知识库的读写与检索：按模块调用 API，支持知识库、笔记、搜索与文件导入

![Type](https://img.shields.io/badge/type-Agent%20Skill-4a6b7c)
![Upstream](https://img.shields.io/badge/upstream-ima-skills%20v1.1.9%20-%20腾讯%20ima（ima.qq.com）-8f8a80)
![License](https://img.shields.io/badge/license-归原作者-b8935a)

> ⚠️ 本仓库是个人使用环境中的 Skill 归档副本，**版权归原提供方**：ima-skills v1.1.9 · 腾讯 ima（ima.qq.com）

## 这是什么

腾讯 ima 笔记与知识库的能力封装：读、写、检索。是 [`wechat-deposit`](https://github.com/px-pangu/wechat-deposit)、[`ima-knowledge-loop`](https://github.com/px-pangu/ima-knowledge-loop) 这两个沉淀类 Skill 的**底层执行层**。

## 模块决策表

| 要做的事 | 走哪个模块 |
|---|---|
| 列知识库 / 建知识库 | 知识库模块 |
| 写入一条笔记 / 卡片 | 笔记写入模块 |
| 检索已有内容 | 搜索模块 |
| 导入本地文件 | 文件导入模块 |
| 读取某篇笔记全文 | 读取模块 |

`SKILL.md` 顶部有 **MANDATORY RULES**：任何操作前必须先读，避免误写、误删与超长内容截断。

## 凭据与调用

凭据通过执行时的 options JSON 传入，**不落盘、不进仓库**。调用走 `ima_api.cjs`：

```bash
node ima_api.cjs --module <模块> --options '<JSON>'
```

正常响应走 stdout；错误走 stderr，返回结构化 `{"code": -100|-200, "msg": "..."}`。

## 目录结构

```
ima-skills/
├─ SKILL.md          强制规则 · 模块决策表 · 凭据检查 · 调用模板
├─ ima_api.cjs       API 调用入口
├─ meta.json / workbuddy.json
└─ _icon.png
```

## 许可

该 Skill 由腾讯 ima 官方提供，著作权归原提供方所有。本仓库仅为个人归档，**不作出任何再许可**，详见 `NOTICE.md`。


## 安装

```bash
git clone https://github.com/px-pangu/ima-skills.git ~/.workbuddy/skills/ima-skills
# Claude Code：~/.claude/skills/ima-skills
```

> 若原包依赖 CLI（如 `kdocs`、`ima`、`wecom`、`pdfkit`），需先按 `SKILL.md` 的安装与认证段落配置本机环境。**仓库内不含任何凭据。**

