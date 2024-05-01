---
title: "测试效果"
showDate: false
showDateUpdated: false
showWordCount: false
showReadingTime: false
showEdit: false
showPagination: false
draft: true
---

## 从 data 目录读取数据

{{ range $.Site.Data.jazz.bass }}
  {{ partial "artist.html" . }}
{{ end }}

{{ $.Site.Data.jazz.bass }}

## 渲染 partial

  {{ partial "icon.html" "github" }}

## 使用内置方法渲染数学公式

\[
\begin{aligned}
KL(\hat{y} || y) &= \sum_{c=1}^{M}\hat{y}_c \log{\frac{\hat{y}_c}{y_c}} \\
JS(\hat{y} || y) &= \frac{1}{2}(KL(y||\frac{y+\hat{y}}{2}) + KL(\hat{y}||\frac{y+\hat{y}}{2}))
\end{aligned}
\]

## 代码块高亮特定行

```go {linenos=table,hl_lines=[8,"15-17"],linenostart=199}
// GetTitleFunc returns a func that can be used to transform a string to
// title case.
//
// The supported styles are
//
// - "Go" (strings.Title)
// - "AP" (see https://www.apstylebook.com/)
// - "Chicago" (see https://www.chicagomanualofstyle.org/home.html)
//
// If an unknown or empty style is provided, AP style is what you get.
func GetTitleFunc(style string) func(s string) string {
  switch strings.ToLower(style) {
  case "go":
    return strings.Title
  case "chicago":
    return transform.NewTitleConverter(transform.ChicagoStyle)
  default:
    return transform.NewTitleConverter(transform.APStyle)
  }
}
```

## 渲染 ASCII 图像

```goat
--->
```