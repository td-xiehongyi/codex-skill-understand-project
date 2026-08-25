# Understand Project

一个面向 Codex 的只读项目导览 Skill。它帮助用户基于仓库证据建立对陌生软件项目的可靠心智模型：项目解决什么问题、各项技术在项目中承担什么职责、功能如何端到端流动，以及修改前应从哪里开始阅读。

## 适用场景

- 想了解一个项目的用途、架构、目录边界或技术栈。
- 想跟踪某个功能、模块或运行路径的完整流程。
- 想修改或扩展项目，但需要先定位安全的阅读入口和边界。

Skill 会根据请求选择项目概览、完整导览、主题追踪或变更导航模式，并明确区分已确认事实、文档声明、推断和未知项。

## 不适用场景

- 直接实现功能、修复缺陷或重构代码。
- 不依赖具体项目上下文的通用技术问答。
- 未经明确授权就安装依赖、启动服务或修改被分析项目。

## 安装

将仓库中的 `understand-project` 文件夹复制到 Codex 的 Skills 目录中。Windows PowerShell 示例：

```powershell
git clone https://github.com/td-xiehongyi/codex-skill-understand-project.git
Copy-Item -Recurse .\codex-skill-understand-project\understand-project "$env:USERPROFILE\.codex\skills\"
```

如果目标位置已经有同名 Skill，请先备份或确认要替换的版本。重新打开 Codex 后，Skill 即可被自动匹配；也可在对话中显式调用它。

## 使用示例

```text
$understand-project 请用初学者能理解的方式介绍当前项目。

$understand-project 追踪“文件扫描”功能从界面操作到最终结果的流程。

$understand-project 我想给搜索增加筛选条件，应该先从哪些文件和边界开始读？
```

## 目录结构

```text
understand-project/
├── SKILL.md                         # 入口、模式选择与安全边界
├── agents/
│   └── openai.yaml                  # Codex 界面元数据
└── references/
    ├── exploration-workflow.md      # 证据收集与停止规则
    └── explanation-guide.md         # 教学与输出质量要求
```

## 验证

使用 Codex Skill Creator 附带的校验器检查 Skill 结构：

```powershell
$env:PYTHONUTF8 = '1'
python "$env:USERPROFILE\.codex\skills\.system\skill-creator\scripts\quick_validate.py" .\understand-project
```

`PYTHONUTF8` 用于避免 Windows 默认编码影响 UTF-8 文本的读取。


