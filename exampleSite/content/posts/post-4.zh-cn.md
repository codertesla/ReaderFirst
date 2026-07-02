+++
title = '欢迎使用 ReaderFirst'
date = 2023-04-20T09:00:00-07:00
draft = false
tags = ['meta']
toc = true
+++

一款同时为人类读者与 AI 智能体设计的、阅读为先、速度为先的 Hugo 主题。这篇文章用于演示目录、各级标题与代码块在中文环境下的表现。

## 为什么再做一个主题

大多数主题依赖大量 JavaScript 与外部 CDN。ReaderFirst 内联一份不到 10KB 的样式表，默认不加载任何外部脚本。

### 设计原则

- 阅读体验优先：宽松行距、收窄行宽、高对比度。
- 速度优先：无第三方 JS、CSS 内联、Lighthouse 100/100 触手可及。
- 人与 AI 友好：语义化 HTML5 与 Schema.org JSON-LD。

## 一段代码示例

下面是一小段 JavaScript，使用 Chroma 语法高亮渲染，并附带复制按钮：

```javascript
function greet(name) {
  // 返回一句友好的问候
  const message = `你好，${name}！`;
  return message;
}

console.log(greet("ReaderFirst"));
```

再来一段 Go 代码：

```go
package main

import "fmt"

func main() {
  for i := 0; i < 3; i++ {
    fmt.Printf("第 %d 行\n", i)
  }
}
```

## 中英文混排

ReaderFirst 自动处理中文与 Latin 字母、数字之间的间距：例如 ReaderFirst 这个名字、Hugo 0.158.0 这个版本号，都会在汉字之间留出恰当空隙。行首标点悬挂、行尾全角标点压缩也已启用。

## 写在最后

切换主题、复制一段代码，然后享受页面瞬时加载带来的安静。
