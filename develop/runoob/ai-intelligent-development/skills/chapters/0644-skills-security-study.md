# Skills（技能）：Skills 权限与安全控制

- 来源：[Skills 权限与安全控制](https://www.runoob.com/skills/skills-security.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：学习笔记
- 章节序号：0644

## 本章内容

Skills 可以访问文件系统、调用外部 API、执行脚本，这些能力如果被滥用会带来安全风险。

本篇介绍如何在设计阶段建立安全边界，防止 Skill 做出超出预期的操作。


## Skills 的默认权限范围

在 Claude 的执行环境中，Skills 的权限由沙箱环境决定，并非无限制的。

Skills 在设计上是"最小权限"原则的实践：Skill 只能访问它明确需要的资源。如果一个 Skill 需要超出上述范围的权限，应当重新考虑设计方案。


## 在 SKILL.md 中明确权限边界

在 Skill 文档中清晰声明它会访问哪些资源，让用户在使用前了解 Skill 的行为范围。

```text
## 权限说明

本 Skill 会进行以下操作，请确认你已了解：

**文件访问**
- 读取：/mnt/user-data/uploads/ 下用户上传的文件
- 写入：/mnt/user-data/outputs/ 下的输出文件

**网络访问**
- 无（本 Skill 不访问任何外部网络）

**不会进行的操作**
- 不读取系统文件
- 不修改已上传的原始文件
- 不访问任何外部服务
```


## 防止路径穿越攻击

当脚本接受用户提供的文件路径时，需要验证路径是否在允许范围内，防止用户通过 ../ 访问到不应访问的目录。


## 实例

```text
通过：/mnt/user-data/uploads/runoob.csv
已拦截：拒绝访问：/mnt/user-data/uploads/../../etc/passwd
只允许读取以下目录：['/mnt/user-data/uploads', '/mnt/skills/public']
```


## API 密钥的安全存储

不同的密钥管理方式，安全等级差异显著。


## 实例


## 输入内容的安全过滤

当 Skill 将用户输入传递给 Shell 命令时，必须对输入进行转义，防止命令注入。


## 实例

永远不要用 os.system(f"cmd {user_input}") 这种方式执行命令。用户输入中若包含 ; rm -rf / 之类的内容，会导致灾难性后果。始终使用 subprocess 的列表参数形式。


## 复习重点

- 能说明 `Skills 权限与安全控制` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
