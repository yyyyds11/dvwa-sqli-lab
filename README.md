# 🧪 DVWA SQL 注入漏洞复现实验

本项目基于 DVWA 靶场环境，复现了 **SQL Injection（SQL 注入）** 漏洞。通过构造 SQL payload 实现认证绕过、数据库信息泄露，记录了完整操作过程与修复建议，并附带截图报告，适合作为 Web 安全学习作品集中的一环。

---

## 📌 实验简介

- 📅 日期：2025 年 xx 月 xx 日  
- 💻 系统环境：Kali Linux（物理机）  
- 🌐 靶场平台：DVWA (Damn Vulnerable Web Application)  
- 🐛 漏洞模块：SQL Injection  
- 🔧 难度：Low / Medium / High（根据你测试的等级填写）

---

## 🔍 实验内容

| 内容             | 描述                                                  |
| ---------------- | ----------------------------------------------------- |
| 🔎 注入测试       | 使用 `' or '1'='1` 绕过用户 ID 过滤，回显多条用户数据 |
| 🐚 数据库信息泄露 | 使用 `UNION SELECT` 披露 MySQL 版本等信息             |
| 📸 截图记录       | 所有测试过程截图见 `screenshots/` 文件夹              |
| 🧾 详细报告       | 复现实验细节见 `report/SQLi漏洞复现报告.md`           |

---

## 🛡 修复建议（摘要）

- 使用预处理语句（如 PDO、mysqli）避免拼接 SQL
- 对用户输入进行白名单校验与过滤
- 不返回 SQL 报错信息，避免泄露数据库结构

详见报告：[`report/SQLi漏洞复现报告.md`](./report/SQLi漏洞复现报告.md)

---

## 📚 参考资料

- [OWASP: SQL Injection](https://owasp.org/www-community/attacks/SQL_Injection)
- [DVWA GitHub 项目](https://github.com/digininja/DVWA)

---

本项目为个人 Web 安全实战训练的一部分，持续更新中 🔧  
欢迎参考、建议与交流！