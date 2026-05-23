# Pre-Open Source

[English README](README.md)

[![罐头实验室](https://world.guantou.site/badge.svg?theme=dark&accent=red&lang=zh&size=sm)](https://world.guantou.site/)

这是一个用于项目开源前准备的 Codex skill。它把开源当作安全、文档、许可和产品发布准备任务，而不是最后随便补一个 README。

## 它适合做什么

- 进行只读的开源前体检。
- 检查敏感内容和仓库卫生。
- 给出 LICENSE、README、CONTRIBUTING、CODE_OF_CONDUCT、issue template、PR template 和 `.gitignore` 建议。
- 当 Git 历史可能包含密钥或私有资产时，建议干净迁移到新公开仓库。
- 输出实用的发布准备报告。

## 安装

```bash
git clone https://github.com/Leochens/skill-pre-open-source.git ~/.codex/skills/pre-open-source
```

然后可以这样告诉 Codex：

```text
Use $pre-open-source to prepare this repository for open sourcing.
```

## 使用说明

这个 skill 在评估类任务里会先只读检查。删除文件、重写历史、推送、发布或暴露疑似密钥等操作，都需要用户明确确认。

`references/checklist.md` 覆盖项目基础信息、README、许可证、敏感内容、`.gitignore`、贡献文档、issue/PR 模板、测试、演示、质量、发布准备和最终公开检查。

## 仓库结构

```text
SKILL.md                    Skill 指令
agents/openai.yaml          Codex UI 元数据
references/checklist.md     完整开源准备清单
```

## 了解更多罐头实验室项目

这个 skill 是 GuanTou Lab 个人 agent 工作流工具箱的一部分。可以访问 [罐头的世界](https://world.guantou.site/) 查看更多项目和产品。

## 开源协议

MIT License。见 [LICENSE](LICENSE)。
