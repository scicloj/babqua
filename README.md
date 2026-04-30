# Babqua

Babqua is a [Quarto](https://quarto.org) extension for writing
[Babashka](https://babashka.org) code in visual documents. Each
`{.clojure .bb}` block in a `.qmd` file is evaluated by Babashka during
rendering, producing code output, charts, diagrams, tables, or computed
HTML.

Babqua is a sibling of [Janqua](https://github.com/scicloj/janqua), the
same idea applied to [Jank](https://jank-lang.org). Where Janqua targets
Jank's emerging ecosystem, Babqua leans on Babashka's batteries — fast
startup, built-in JSON / Hiccup / EDN, and the [pods](https://github.com/babashka/babashka/blob/master/doc/projects.md#pods)
ecosystem (SQLite, AWS, HTML parsing, …) — to make notebooks
self-contained and reproducible.

Charts render via Plotly, Vega-Lite, ECharts, Cytoscape, or Highcharts;
diagrams via Mermaid and Graphviz; tables via Pandoc. Rendering follows
the [Kindly](https://scicloj.github.io/kindly-noted/) convention, the
same way [Clay](https://scicloj.github.io/clay/) handles Clojure docs.

> **Experimental** — this project is at an early stage. Currently
> developed and tested on Linux. Feedback and ideas are welcome via
> GitHub issues or the [Scicloj Zulip chat](https://scicloj.github.io/docs/community/chat/).

## Prerequisites

- [Quarto](https://quarto.org/docs/get-started/)
- [Babashka](https://github.com/babashka/babashka#installation)

That's it. No JVM, no `bbin`, no nREPL client to install.

## Quick start

Install the extension in your project:

```bash
quarto add scicloj/babqua
```

Create `hello.qmd`:

````markdown
---
title: "Hello Babashka"
filters:
  - bb
---

```{.clojure .bb}
(+ 1 2 3)
```

```{.clojure .bb}
^:kind/hiccup
[:div {:style "color: coral; font-size: 24px;"} "Hello from Babashka!"]
```
````

Render it:

```bash
quarto render hello.qmd
```

## License

MIT
