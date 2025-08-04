

```
~/.config/nvim/
├── init.lua
├── lua/
│   ├── plugins/                        <-- All plugin configs
│   │   ├── alpha.lua                   <-- Dashboard UI
│   │   ├── colorscheme.lua             <-- Theme setup
│   │   ├── keymaps.lua                 <-- Custom keymaps
│   │   ├── lsp.lua                     <-- Language Server setup
│   │   ├── treesitter.lua              <-- Syntax highlighting
│   │   ├── comment.lua                 <-- Toggle comments
│   │   ├── todo.lua                    <-- TODO Comments
│   │   ├── nvimtree.lua                <-- File explorer
│   │   ├── markdown.lua                <-- Markdown preview
│   │   ├── git.lua                     <-- Git tools
│   │   ├── ui.lua                      <-- statusline, winbar, etc.
│   │   └── extras.lua                  <-- Optional plugins
│   └── config/
│       ├── options.lua                 <-- Vim options
│       ├── autocmds.lua                <-- Autocommands
│       ├── lazyvim.lua                 <-- LazyVim-specific config override
├── stylua.toml                         <-- Lua formatter config
├── lazy-lock.json                      <-- Lazy plugin lock file
└── README.md                           <-- (Optional) Documentation

```


---

