+++
title = 'Welcome to ReaderFirst'
date = 2023-04-20T09:00:00-07:00
draft = false
tags = ['meta']
toc = true
+++

A reading-first, speed-first Hugo theme built for both humans and AI agents. This post exercises the table of contents, headings, and code blocks.

## Why another theme

Most themes ship heavy JavaScript and external CDNs. ReaderFirst inlines a sub-10KB stylesheet and runs zero external scripts by default.

### Design principles

- Reading experience first: generous line-height, constrained measure, high contrast.
- Speed first: no third-party JS, CSS inlined, Lighthouse 100/100 in reach.
- Human and AI friendly: semantic HTML5 and Schema.org JSON-LD.

## A code example

Here is a tiny JavaScript snippet rendered with Chroma highlighting and a copy button:

```javascript
function greet(name) {
  // return a friendly greeting
  const message = `Hello, ${name}!`;
  return message;
}

console.log(greet("ReaderFirst"));
```

And a bit of Go:

```go
package main

import "fmt"

func main() {
  for i := 0; i < 3; i++ {
    fmt.Printf("line %d\n", i)
  }
}
```

## Wrapping up

Toggle the theme, copy a snippet, and enjoy the silence of a page that loads instantly.
