# Changelog

All notable changes to babqua will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## Unreleased

## v0.1.1

### `:kind/table` renders as a Pandoc pipe table

`:kind/table` previously emitted a raw `<table>` HTML fragment built
from hiccup. It now emits Pandoc pipe-table markdown, so Quarto's
native table styling (striped rows, hover highlight, responsive
layout, theme adaptation) applies automatically. No author-side
change is required. Cell values containing `|` are escaped; embedded
newlines render as `<br>`.

### Mermaid diagrams carry a `.mermaid` class

The `<div>` that holds a rendered Mermaid SVG now has
`class="mermaid"`, so downstream stylesheets (e.g. Clojure Civitas's
dark-mode `body.quarto-dark .mermaid { filter: invert(...) }` rule)
can target Babqua-rendered diagrams without further wiring.

## v0.1.0

First public release. Quarto-extension API for evaluating Babashka
code blocks (`{.clojure .bb}`) in `.qmd` documents, with Kindly-driven
rendering for hiccup, HTML, markdown, charts (Plotly, Vega-Lite,
ECharts, Cytoscape, Highcharts), diagrams (Mermaid, Graphviz), TeX,
tables, and code. Optional persistent-nREPL preview mode keeps state
warm across saves.
