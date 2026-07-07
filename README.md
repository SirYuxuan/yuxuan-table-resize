# 雨轩表格列宽 (Yuxuan Table Resize)

一个 Obsidian 插件：拖动表格列边框调整列宽，列宽跨会话保存。

这是在 [Table Column Resize](https://github.com/lolieatapple)（作者 **lolieatapple**）基础上的本地改造版，主要解决**表格被强制撑满整页**的问题。

## 与原版的区别

原版为了实现列宽拖动，用 `table-layout: fixed !important; width: 100% !important` 把每张表都强制拉满页面宽度。本版改成：

- **宽度跟内容走**：没拖过列宽的表格保持 Obsidian 原生尺寸——短表格就窄、文字正常换行，不再占满整页。
- **钉住态才固定**：只有「已保存列宽」或「正在拖动」的表格才切换到 `table-layout: fixed` + `width: max-content`，此时表格总宽 = 各列宽度之和。
- **超宽横向滚动**：各列之和超过可用宽度时，表格被包进一层 `overflow-x: auto` 的容器，在**表格内部横向滚动**，而不是撑破页面。

## 安装

手动安装：把 `main.js`、`manifest.json`、`styles.css` 放进
`<你的库>/.obsidian/plugins/yuxuan-table-resize/`，
然后在 设置 → 第三方插件 中启用「雨轩表格列宽」。

## 使用

- 把鼠标移到表头列的右边框，出现高亮手柄即可左右拖动调整列宽。
- 列宽自动保存，重开笔记仍在。
- 设置里可调「最小列宽」，或一键「重置全部宽度」（重置后表格回到原生的内容自适应宽度）。

## 说明

- 本仓库不包含 `data.json`（列宽保存数据），那是各人本地的运行时状态。
- 因为改了插件 `id`（`yuxuan-table-resize`），它不会被 Obsidian 社区插件市场自动更新覆盖。
- 原版权归 lolieatapple 所有，本版仅为个人使用的衍生改造；如需再分发，请遵循上游项目的许可协议。
