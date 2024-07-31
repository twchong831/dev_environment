# Vim to flutter setting progress

- using mac vim

## plugin

### vim-plug Tool

- install
  
[vim-plug](https://github.com/junegunn/vim-plug)

```bash
cd ~/.vim
mkdir autoload
cd autoload
wget https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

### plug setting in vimrc

- setting in ~/.vimrc (macVim & MacOS)

```vim
"=========plugin================
call plug#begin()

" File and folder management
Plug 'preservim/nerdtree'
Plug 'tiagofumo/vim-nerdtree-syntax-highlight'
Plug 'PhilRunninger/nerdtree-visual-selection'

" Snippets
Plug 'SirVer/ultisnips'
Plug 'honza/vim-snippets'
Plug 'natebosch/dartlang-snippets'

" Language support
Plug 'tpope/vim-projectionist'
Plug 'neoclide/coc.nvim', {'branch': 'release'}
Plug 'jiangmiao/auto-pairs'

" Editor Configuration
Plug 'editorconfig/editorconfig-vim'

"theme tokyonight
Plug 'ghifarit53/tokyonight-vim'

" Dart
Plug 'dart-lang/dart-vim-plugin'

" Flutter
Plug 'thosakwe/vim-flutter'
Plug 'natebosch/vim-lsc'
Plug 'natebosch/vim-lsc-dart'
Plug 'f-person/nvim-sort-dart-imports'

" Git
Plug 'tpope/vim-fugitive'
Plug 'Xuyuanp/nerdtree-git-plugin'
Plug 'APZelos/blamer.nvim'

" Statusline
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'

" Rainbow Parentheses
Plug 'luochen1990/rainbow'

" Indent Guide
Plug 'Yggdroot/indentLine'

" Surround
Plug 'tpope/vim-surround'

" Repeat
Plug 'tpope/vim-repeat'

" Commentary
Plug 'tpope/vim-commentary'

" Devicons
Plug 'ryanoasis/vim-devicons'

call plug#end()
"=========!pluging==============
```

### plug install

```vim
:PlugInstall
```
