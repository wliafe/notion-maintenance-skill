# notion-maintenance-skill

通过 **Notion MCP** 主动查找并阅读页面中的「使用说明」，再按其中要求读写、整理 Notion 内容的通用 Agent Skills 技能。

技能**不包含**维护手册正文，只教如何找到名为「使用说明」的章节并照做。手册规则、授权与归属约定始终以 Notion 现场为准；你改 Notion 或改手册时，不必同步改本仓库正文。

## 使用条件

- AI 客户端能够加载技能说明，并支持调用 Notion MCP（搜索、读取、更新等）。
- 已连接正确的 Notion 工作区；首次使用通常需要在客户端完成 Notion 授权。
- 目标页面上存在标题为 **「使用说明」** 的手册章节（入口页与各分区页）。

## 安装

```bash
npx skills add wliafe/notion-maintenance-skill
```

## 加载技能

也可用手动方式：将包含 `SKILL.md` 和 `references/` 的完整 `notion-maintenance-skill` 目录，放到当前客户端实际支持的技能位置或通过其技能管理方式导入，再按该客户端要求重新加载。

技能遵循 [Agent Skills 规范](https://agentskills.io/specification)。不同客户端的技能发现方式和调用语法不同，不保证所有支持 MCP 的客户端也会自动发现技能。不支持自动加载时，可手动把 `SKILL.md` 及按需引用的说明提供给 AI。

**技能加载与 Notion MCP 连接是两件事。** AI 先检查现有工具与授权；缺少连接时说明缺项，条件齐备且已有明确授权时再协助配置。仅触发技能或要求整理 Notion，不自动授权安装。

具体检查步骤见 [MCP 检查与连接](references/mcp-setup.md)。

## 使用示例

- “按手册整理知识库里和本次任务相关的部分。”
- “更新工作方式里对应条目前，先读使用说明再改。”
- “在项目页补实验记录，按使用说明写并回读核对。”
- “Notion 里找不到使用说明时，说明你是怎么找的。”

若客户端支持按技能名称显式调用，可使用该客户端提供的方式选择 `notion-maintenance-skill`；核心说明不依赖某一种调用语法。

## 查找约定

1. 搜索标题含「工作台」或用户指定的入口页并读取。
2. 在入口与目标分区定位 **「使用说明」**；分区若要求先读上级，则先读上级。
3. 严格按已读「使用说明」搜索现有内容、做最小修改、回读验收。
4. 找不到章节时停止臆造规则，向用户确认入口或章节名。

详细步骤见 [查找「使用说明」](references/finding-usage-guide.md)。

## 文件结构

```text
notion-maintenance-skill/
├── SKILL.md
├── references/
│   ├── mcp-setup.md
│   └── finding-usage-guide.md
├── README.md
└── LICENSE
```

## 官方资料

- [Notion MCP 文档](https://developers.notion.com/docs/mcp)
- [Agent Skills 规范](https://agentskills.io/specification)

## 许可证

本技能采用 [MIT License](LICENSE)。
