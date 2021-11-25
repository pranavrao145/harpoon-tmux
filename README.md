# harpoon-tmux
A plugin for [ThePrimeagen/harpoon](https://github.com/ThePrimeagen/harpoon) to add integration between tmux and harpoon. This plugin supports all the operations in harpoon's `term` module, but with tmux terminals rather than Neovim terminals.

## Installation
This plugin depends on harpoon (obviously) to function. If you're using vim-plug:

```vim
Plug 'nvim-lua/plenary.nvim' " this is a dependency for both harpoon and harpoon-tmux
Plug 'ThePrimeagen/harpoon'
Plug 'pranavrao145/harpoon-tmux'
```

## Usage
Below is the usage of this plugin:

### Setup
This plugin introduces one extra harpoon configuration option, `tmux_autoclose_windows`, which can be set in harpoon's setup function itself. If `tmux_autoclose_windows` is set to `true`, harpoon-tmux will automatically close any tmux windows it creates when Neovim closes. When set to `false` (as it is by default), nothing will happen when Neovim closes and any windows created will be abandoned.

#### Example Harpoon Config
```lua
require("harpoon").setup({
    global_settings = {
        -- other config options
        tmux_autoclose_windows = false
    },
    -- other config
})
```
### Available Functions
harpoon-tmux functions are called in the exact same way as functions from `harpoon.term`. They also share a configuration, so commands you set for `harpoon.term` will automatically be adopted by harpoon-tmux.

#### Example Usage
```lua
-- goes to the first tmux window
lua require("harpoon-tmux").gotoTerminal(1)

-- sends commands to the first tmux window
lua require("harpoon-tmux").sendCommand(1, 1)
lua require("harpoon-tmux").sendCommand(1, "ls -la")
```
