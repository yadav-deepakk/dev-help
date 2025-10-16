## Setting up NeoVim on MacOS
1. `bob` the neovim management tool - [bob](https://github.com/MordechaiHadad/bob)
   > set $PATH for bob in `.zshrc` file once installed.
   > commands for using `bob`
   ```
   brew install bob 
   bob help 
   bob install stable
   bob install nightly
   bob list
   bob use <nvim-version>
   ```

2. package manager used in `neovim`
   ```
   lazyVim
   ```
   
4. `plugins` used for `nvim` editor
  ```
  {
    "lazy.nvim",
    "vague", 
    "nvim-web-devicons",
    "nvim-treesitter",
    "plenary.nvim",
    "telescope.nvim"
  }
  ```
---


### 1. Install NeoVim `nvim`
  ```
  brew install neovim
  ```

### 2. Create `~/.config/nvm/init.lua` file 
- this file will have initialization code for nvim. 
  ```
  touch init.lua
  ```
- this file will have lua code and necessary imports related to nvim configs. 

### 3. create keybindings 
- create `keymaps.lua` file in `~/.config/nvim/lua/core/` add vim configure options, keybindings.
  ```
  vim.g.mapleader = ' '
  vim.g.maplocalleader = ' '
  
  vim.opt.backspace = '2'
  vim.opt.showcmd = true
  vim.opt.laststatus = 2
  vim.opt.autowrite = true
  vim.opt.cursorline = true
  vim.opt.autoread = true
  
  -- use spaces for tabs and whatnot
  vim.opt.tabstop = 2
  vim.opt.shiftwidth = 2
  vim.opt.shiftround = true
  vim.opt.expandtab = true
  
  vim.keymap.set('n', '<leader>h', ':nohlsearch<CR>')
  ```
  
- add below code inside `init.lua`
  ```
  require("core.keymaps")
  ```

### 4. Installing `packer`
- create a `~/.config/nvim/lua/core/plugins.lua` file and below code. It is called, [Bootstrap](https://github.com/wbthomason/packer.nvim?tab=readme-ov-file#bootstrapping) method to have packer for `nvim`. 
  ```
  local ensure_packer = function()
    local fn = vim.fn
    local install_path = fn.stdpath('data')..'/site/pack/packer/start/packer.nvim'
    if fn.empty(fn.glob(install_path)) > 0 then
      fn.system({'git', 'clone', '--depth', '1', 'https://github.com/wbthomason/packer.nvim', install_path})
      vim.cmd [[packadd packer.nvim]]
      return true
    end
    return false
  end
  
  local packer_bootstrap = ensure_packer()
  
  return require('packer').startup(function(use)
    use 'wbthomason/packer.nvim'
    -- My plugins here
    -- use 'foo1/bar1.nvim'
    -- use 'foo2/bar2.nvim'
  
    -- Automatically set up your configuration after cloning packer.nvim
    -- Put this at the end after all plugins
    if packer_bootstrap then
      require('packer').sync()
    end
  end)
  ```
- above my plugin section is used to import all plugins theat you want in neovim 
- add below code inside `init.lua`
  ```
  require("core.plugins")
  ```
- two useful commands for packer are `PackerStatus` and `PackerSync`. `PackerSync` will install/pull-latest packages and `PackerStatus` gives all list of packages.
  
5. add `color-scheme`, `nvm-tree`, `icons`, `lualine`
- add below line in `plugins.lua` file below `use 'wbthomason/packer.nvim'` line
  ```
  use 'ellisonleao/gruvbox.nvim'
  use 'nvim-tree/nvim-tree.lua'
  use 'nvim-tree/nvim-web-devicons'
  use 'nvim-lualine/lualine.nvim'
  ```
- then you can do _PackerSync_
  ```
  :PackerSync
  ```
  
6. create a directory `gruvbox.lua`, `lualine.lua`, `nvim-tree` inside directory `~/.config/nvim/lua/core/plugin_config`
- gruvbox.lua
  ```
  vim.o.termguicolors = true
  vim.cmd([[colorscheme gruvbox]])
  ```
- lualine.lua
  ```
  require('lualine').setup {
    options = {
      icons_enabled = true,
      theme = 'gruvbox',
    },
    sections = {
      lualine_a = {
        {
          'filename',
          path = 1,
        }
      }
    }
  }
  ```
- nvim-tree
  ```
  vim.g.loaded_netrw = 1
  vim.g.loaded_netrwPlugin = 1
  
  require("nvim-tree").setup()
  
  vim.keymap.set('n', '<c-n>', ':NvimTreeFindFileToggle<CR>')
  ```
- init.lua
  ```
  require('core.plugin_config.gruvbox')
  require('core.plugin_config.lualine')
  require('core.plugin_config.nvim-tree')
  ```


7. 

 
### LSP (Language Server Protocol) 
LSP - Language server protocol is used in IDEs to provide features related to code completions, syntax checking, refractoring and references more
- java and Spring boot: eclise JDT Language server (JDTLS) is used in neovim
- 

---
### Useful links 
- [Awsome NeoVim](https://github.com/rockerBOO/awesome-neovim)
- [gruvbox](https://github.com/morhetz/gruvbox)
- [lualine](https://github.com/nvim-lualine/lualine.nvim)
- [telescope](https://github.com/nvim-telescope/telescope.nvim)
