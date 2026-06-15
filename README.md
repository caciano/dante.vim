# dante.nvim

A warm, dark colorscheme for Neovim — black canvas, peachpuff foreground, teal comments,
gold keywords, green types, olive functions, red strings. Easy on the eyes for long reading
and writing sessions.

> Originally written in **2002** as `dante.vim` by Caciano Machado, and revived in **2026**
> with a fully modern highlight set: Tree-sitter, LSP semantic tokens, diagnostics, and
> first-class support for a contemporary plugin stack.

Requires Neovim **0.8+** and **truecolor** (`termguicolors`).

---

## Why dante

The palette was hand-tuned decades ago for comfortable programming on a dark background, and
it still holds up. This revival keeps that exact identity while modernizing the mechanics:

- Named X11 colors resolved to hex.
- Contrast lifted where the original ran low (the olive functions and the deep blue preproc),
  so every code color clears a **≥ 4.5:1** contrast ratio against the background (WCAG AA).
- Dated choices fixed: folds no longer use a white background, and Visual selection is a solid
  warm highlight instead of reverse video.
- Comfort groups the original lacked: `CursorLine`, a highlighted current-line number,
  a subtle `ColorColumn`, `MatchParen`, and a readable completion menu.

---

## Features

- Editor / UI, legacy Vim syntax groups
- **Tree-sitter** (`@function`, `@keyword`, `@string`, `@variable.member`, markup headings, …)
- **LSP semantic tokens** (`@lsp.type.*`, inheriting from the Tree-sitter groups)
- **Diagnostics** (error / warn / info / hint, with undercurl and virtual-text tints)
- **Diff & Git** including gitsigns
- **Plugin support**: blink.cmp, which-key, fzf-lua, oil.nvim, indent-blankline, markview,
  and dimmed Copilot ghost text
- Spell groups

---

## Palette

| Role | Color | Hex |
|------|-------|-----|
| Background | near-black | `#0a0a0a` |
| Foreground (reading) | peachpuff tan | `#cdaf95` |
| Comments | teal | `#1f9f9f` |
| Keywords / statements | gold | `#d2b21a` |
| Types | green | `#83c44d` |
| Functions | olive | `#a6b56e` |
| Strings / constants | red | `#df574a` |
| Numbers / errors | bright red | `#ee4b3b` |
| Booleans / built-ins | orange | `#e0894a` |
| Preprocessor / directories | blue | `#5a8fd6` · `#6a8fff` |
| Special / delimiters | brown | `#c87f4a` |
| Titles | aquamarine | `#79e8c4` |
| Members / links | purple | `#9d7cd8` |
| Search / current line | goldenrod | `#eead0e` |

---

## Installation

### Option A — drop-in file (no plugin manager)

```bash
mkdir -p ~/.config/nvim/colors
cp dante.lua ~/.config/nvim/colors/dante.lua
```

### Option B — lazy.nvim

```lua
{ "caciano/dante.nvim", lazy = false, priority = 1000,
  config = function() vim.cmd.colorscheme("dante") end }
```

For a plugin repo, place the file at `colors/dante.lua` so Neovim finds it on the runtimepath.

---

## Usage

```lua
vim.opt.termguicolors = true
vim.cmd.colorscheme("dante")
```

With [lualine](https://github.com/nvim-lualine/lualine.nvim), use `theme = "auto"` and the
statusline follows dante automatically.

---

## Customization

The full palette is a single table at the top of `dante.lua`. Change one value and every
group that uses it updates:

```lua
local c = {
  bg     = "#0a0a0a",  -- set "#000000" for true black
  fg     = "#cdaf95",
  gold   = "#d2b21a",
  olive  = "#a6b56e",
  -- …
}
```

For example, members/properties are purple (`@variable.member`) to set them apart; point that
group at `c.fg` or `c.olive` if you prefer a flatter look.

---

## Compatibility notes

- Truecolor only — set `vim.opt.termguicolors = true` and use a terminal that supports it.
- LSP semantic-token and Tree-sitter groups need their respective features enabled; without
  them, the legacy syntax groups still render correctly.

---

## Credits

Original `dante.vim` (2002) and the palette: **Caciano Machado**. Modernized highlight set: 2026.

## License

Released under the MIT License.

