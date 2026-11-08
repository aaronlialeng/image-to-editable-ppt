# 图片转可编辑 PPT（image-to-editable-ppt）

把幻灯片图片、截图、AI 生成页或扁平化 PPT 重建为**可编辑** PowerPoint：保留原图构图与文案，交付 PPTX、预览和验收报告。

作者：李想

## 安装（Codex）

在 Codex 里执行：

```text
$skill-installer install https://github.com/aaronlialeng/image-to-editable-ppt/tree/main/skills/image-to-editable-ppt
```

或用 Skills CLI：

```bash
npx skills add aaronlialeng/image-to-editable-ppt
```

安装后重启 Codex（如技能未出现）。然后可用：

```text
$image-to-editable-ppt 把这张图重建为可编辑 PPT，保留构图和文案，交付 PPTX、预览和验收报告。
```

也可把 skill 文件夹复制到 `~/.agents/skills/image-to-editable-ppt`（全局）或项目内 `.agents/skills/`。

## 核心规则

- **禁止**把源图整页贴进最终幻灯片当成品
- 用原生可编辑对象重建：文本框、形状、线条、表格、图表标签、独立图标/Logo
- 复杂照片、吉祥物、产品图、官方 Logo 可保留为**独立**图片对象
- 看不清的字或数据不要瞎猜；标注未确认项

## 必交付物

```text
editable_rebuild.pptx
preview.png 或 preview.pdf
audit_report.md
```

## 验收

详见 `skills/image-to-editable-ppt/references/acceptance.md`。

分开报告：文案核对、可编辑性、视觉保真、字体、最终渲染器。允许状态：`passed` / `pending confirmation` / `failed` / `not checked`。

若当前环境没有本机 Microsoft PowerPoint，最终 PowerPoint 验收必须标为 **not checked**，不得宣称已通过。

## 仓库结构

```text
.
├── README.md
├── plugin.json
├── .codex-plugin/plugin.json
└── skills/image-to-editable-ppt/
    ├── SKILL.md
    ├── agents/openai.yaml
    └── references/acceptance.md
```

## 许可

MIT
