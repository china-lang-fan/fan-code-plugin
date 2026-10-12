# 凡语言 VS Code 插件

[凡语言](https://china-lang-fan.github.io/) 的 Visual Studio Code 支持插件。

## 功能

- 语法高亮：中文关键字、中文/符号运算符、类型、内置函数、字符串、数字和注释
- 代码片段：条件、判断、循环、函数、模型、方法、错误处理和模块导入
- 括号与引号自动闭合、配对
- `#` 注释切换（`Ctrl + /`）
- 基于缩进和 `结束` 的代码折叠
- 一键运行当前 `.凡` 脚本
- 启动交互式 REPL
- 实时诊断（内置语言服务器 LSP）：语法错误、分段函数段间空格等波浪线提示

## 下载和安装

可以从 [最新构建](https://github.com/china-lang-fan/fan-code-plugin/releases/tag/latest) 下载 `.vsix` 文件。

在 VS Code 中选择扩展面板右上角的“从 VSIX 安装”，也可以通过命令行安装下载得到的 `.vsix` 文件。

## 前提

运行脚本和 REPL 需要先安装凡语言解释器：

```sh
fan version
```

安装方式见[官方文档](https://china-lang-fan.github.io/guide/getting-started)。

## 使用

- 打开 `.凡` 文件后，点击编辑器右上角运行按钮
- 或打开命令面板，执行：
  - `fan: 运行当前脚本`
  - `fan: 启动交互式 REPL`

## 扩展设置

| 设置项 | 说明 | 默认值 |
| --- | --- | --- |
| `fan.executablePath` | 凡语言解释器路径 | `fan` |
| `fan.runInTerminal` | 是否在集成终端运行 | `true` |
| `fan.clearBeforeRun` | 运行前是否清空终端 | `false` |
| `fan.languageServer.enable` | 是否启用语言服务器（实时诊断） | `true` |

## 诊断

插件打开 `.凡` 文件后会以后台方式启动 `fan lsp` 语言服务器，实时显示：

- 语法错误（红色波浪线）
- 分段函数段间空格等可能误用的写法（黄色波浪线）

例如分段函数各段必须紧邻，段间不能有空格：

```凡
修改(张三)的状态为无效
```

写成 `修改(张三) 的状态为无效` 时，含义变成“先普通调用 `修改(张三)`，再访问返回值成员”两件事，编辑器会在空格处给出告警。

## 开发

```sh
pnpm install
pnpm typecheck
pnpm build
```

按 `F5` 启动扩展开发宿主。打包 VSIX：

```sh
pnpm package
```

## 许可证

MIT
