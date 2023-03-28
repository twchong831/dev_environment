# Vim to flutter setting progress

- using neovim

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

- setting in init.vim (neovim & MacOS)

```bash
"=========plugin================
call plug#begin()

"theme tokyonight
Plug 'folke/tokyonight.nvim', { 'branch': 'main' }

call plug#end()
"=========!pluging==============

"=========set theme=============
colorscheme tokyonight-night
"===============================

```

- PluginInstall active

```bash
# in neovim
:PluginInstall
```

## font

```bash
brew tap homebrew/cask-fonts
brew isntall --cask font-hack-nerd-font
```

- iterm2의 폰트를 HACK nerd로 변경

## Error

### E5248

- NERDtree hightlight 플러그인 사용 시 해당 오류가 발생하며
- 아이콘이 출력되지 않음 -> 별도의 문제
  - 이는 NERD font 사용으로 해결할 수 있음
- 옵션 추가

```vim
let g:NERDTreeLimitedSyntax = 1
```

## Coc Config

- vim에서 명령어로 해당 명령어를 입력

```vim
:CocConfig
```

[CocConfig](https://www.google.com/search?q=vim-go&rlz=1C5CHFA_enKR1017KR1018&oq=vim-go&aqs=chrome..69i57.301j0j7&sourceid=chrome&ie=UTF-8)

- path : ~/.config/nvim/coc-settings.json

```json
"languageserver": {
  "clangd": {
    "command": "clangd",
    "rootPatterns": ["compile_flags.txt", "compile_commands.json"],
    "filetypes": ["c", "cc", "cpp", "c++", "objc", "objcpp"]
  }
  "dart": {
    "command": "dart",
    "args": [
      " change this to the path of analysis_server
      "/usr/local/opt/dart/libexec/bin/snapshots/analysis_server.dart.snapshot",
      "--lsp",
      "--client-id",
      "vim",
      "--client-version",
      "coc.nvim",
    ],
    "filetypes": ["dart"],
    "trace.server": "verbose"
  },
}
```

## TSInstall

```vim
:TSInstall all
:TSUpdate
```

## ripgrep

```bash
brew install ripgrep
```

## fd

```bash
brew install fd
```

## perl

```bash
cpan App::cpanmnus
sudo cpanm module
```

## languageClient

- ERROR : No pre-built binary available for Darwin arm64. cargo is not available. Abort.
- and not installed using :PlugInstall

### solution

```bash
brew install rust
```

- reinstall
