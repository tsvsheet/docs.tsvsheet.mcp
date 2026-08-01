---
title: tsvsheet.mcp
---

**tsvsheet.mcp** is the [Model Context Protocol](https://modelcontextprotocol.io) server for [tsvsheet](https://github.com/tsvsheet/tsvsheet): the `tsvsheet-mcp` binary exposes the [go-tsvsheet](https://github.com/tsvsheet/go-tsvsheet) engine as MCP tools — evaluate an expression against a sheet, check a sheet for errors, explain a cell's computation, and render or format a `.tsvt` — so AI agents work with spreadsheets through the same engine as every other frontend.

- Source: [tsvsheet/tsvsheet.mcp](https://github.com/tsvsheet/tsvsheet.mcp)
- Engine: [tsvsheet/go-tsvsheet](https://github.com/tsvsheet/go-tsvsheet)
- Language: [tsvsheet/tsvsheet](https://github.com/tsvsheet/tsvsheet)

## Instructions for an agent

The server tells a client, at initialize, what a `.tsvt` is and which tool answers which question. The same text prints on demand, so it can be read or piped into a configuration without starting a server:

```bash
tsvsheet-mcp --instructions
```

It is deliberately about scope rather than parameters — the tool schemas already describe those. It states what each tool does NOT do: `tsvsheet_check` reports unknown function calls and does not validate references, a render result is a view of computed values and never a replacement for the source file, and comment and directive lines occupy no row, so an address is counted in data rows rather than physical lines.
