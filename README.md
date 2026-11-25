# opslymd

Render Markdown in your terminal — like `cat`, but formatted. A single static Go binary, part of [Opsly MD](https://github.com/iaminci/opsly-md).

```bash
opslymd README.md
```

Headings, lists, tables, task lists, blockquotes, links, math, footnotes and syntax-highlighted code blocks are drawn with colors and box characters. Opsly secure code fences (` ```secure `) stay masked unless you pass `--reveal`. Files that aren't Markdown are printed like `cat`, syntax-coloured when colors are on.

## Install

**Homebrew** (once the tap is published):

```bash
brew install iaminci/tap/opslymd
```

**Go 1.26+:**

```bash
go install github.com/iaminci/opslymd-cli/cmd/opslymd@latest
```

**From source:**

```bash
git clone https://github.com/iaminci/opslymd-cli && cd opslymd-cli
go build -o opslymd ./cmd/opslymd
```

## Usage

| Command | Description |
|---------|-------------|
| `opslymd file.md` | Render a file |
| `opslymd a.md b.md` | Render several files in order |
| `opslymd main.go` | Print a non-Markdown file like `cat`, syntax-coloured when colors are on |
| `cat file.md \| opslymd` | Render standard input |
| `opslymd --width 80 file.md` | Wrap at 80 columns (default: terminal width, max 120) |
| `opslymd --reveal file.md` | Show the contents of secure fences |
| `opslymd --color file.md \| less -R` | Keep colors when piping into a pager |

Colors are turned off automatically when output is piped or `NO_COLOR` is set.

## How it works

Parsing uses [goldmark](https://github.com/yuin/goldmark) (GFM, footnotes, math), code highlighting uses [chroma](https://github.com/alecthomas/chroma), and the output is ANSI text. ASCII tree diagrams are kept as code blocks and `json` fences are pretty-printed, matching the Opsly MD web app.

## License

MIT
