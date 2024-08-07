# VIM

## neovim

- 최신 버전 설치 필요

[LINK](https://github.com/neovim/neovim/blob/master/INSTALL.md)

```bash
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim-linux64.tar.gz
# sudo rm -rf /opt/nvim
sudo tar -C /opt -xzf nvim-linux64.tar.gz
```

```bash
# ~/.zshrc
export PATH="$PATH:/opt/nvim-linux64/bin"
```

### nvchad

```bash
git clone https://github.com/NvChad/starter ~/.config/nvim && nvim
```

![nvchad init](image/nvchad.png)

## vim

- mvim 설치

## vimrc

```makefile
set nocompatible              " be iMproved, required
filetype off                  " required
" set the runtime path to include Vundle and initialize
if has("mac")
 "Mac
 "set rtp+=~/.vim/bundle/Vundle.vim
 call plug#begin()
elseif has("win32")
 "all windows
 set rtp+=$HOME/.vim/bundle/Vundle.vim/
 call vundle#begin('$HOME/.vim/bundle/')
elseif has("win32unix")
 "Cygwin
elseif has("bsd")
 "BSD-based, greeBSD
elseif has("linux")
 "Linux
 set rtp+=~/.vim/bundle/Vundle.vim
 call vundle#begin()
end

"LINUX
"WINDOWS
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/.vim/bundle')
" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'
" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
" Plugin 'L9'
" Git plugin not hosted on GitHub
Plugin 'git://git.wincent.com/command-t.git'
" git repos on your local machine (i.e. when working on your own plugin),
"Plugin 'file:///home/jjeaby/Dev/tools/vim-plugin'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
" Plugin 'ascenator/L9', {'name': 'newL9'}
" All of your Plugins must be added before the following line
Plugin 'vim-airline/vim-airline'
Plugin 'scrooloose/nerdtree'
Plugin 'airblade/vim-gitgutter'
Plugin 'scrooloose/syntastic'
Plugin 'ctrlpvim/ctrlp.vim'
Plugin 'ghifarit53/tokyonight-vim'
"Plugin 'Tagbar'
call vundle#end()            " required

"NERDTree ON 단축키를 "\nt"로 설정
map <Leader>nt <ESC>:NERDTree<CR>
let NERDTreeShowHidden=1
" let NERDTreeQuitOnOpen=1
let g:ctrlp_custom_ignore = {
  \ 'dir':  '\.git$\|vendor$',
    \ 'file': '\v\.(exe|so|dll)$'
\ }

" Tag List 환경설정
filetype on                                 "vim filetype on
"Source Explorer 환경설정
nmap <C-H> <C-W>h                           "왼쪽 창으로 이동
nmap <C-J> <C-W>j                           "아래 창으로 이동
nmap <C-K> <C-W>k                           "윗 창으로 이동
nmap <C-L> <C-W>l                           "오른쪽 창으로 이동

nmap <F2> :NERDTreeToggle<CR>
nmap <F3> :TagbarToogle<CR>

nmap <F5> : make all<CR>

" 세부 정보 출력
set nu
set title
set showmatch
set ruler
" 구문 강조 사용
if has("syntax")
 syntax on
endif
" 색깔 설정
set t_Co=256
" 들여쓰기 설정
set autoindent
set smartindent
set tabstop=4
set shiftwidth=4
set softtabstop=4
set smarttab
"set expandtab
set nobackup    "기존

"기존
syn on
set hlsearch

"color
colorscheme darkblue
set autoindent

"set guifont?
if has("mac")
 set guifont=JetBrains\ Mono:h15
 "Mac
elseif has("win32")
 "all windows
elseif has("win32unix")
 "Cygwin
elseif has("bsd")
 "BSD-based, greeBSD
elseif has("linux")
 "Linux
 set guifont=JetBrains\ Mono\ 20
end
" 붙여넣기 설정
set paste
set clipboard=unnamedplus
set mouse=a
" 한글 입력 설정
if has("mac")
 "Mac
elseif has("win32")
 "all windows
 set encoding=cp949
 set fileencodings=utf-8
 set langmenu=cp949
elseif has("win32unix")
 "Cygwin
elseif has("bsd")
 "BSD-based, greeBSD
elseif has("linux")
 "Linux
 set encoding=utf-8  "linux
 set termencoding=utf-8 "linux
end

"들여쓰기
let g:indentLine_color_gui = '#FFF000'
let g:indentLine_color_term = 100
let g:indentLine_char = '¦'
let g:indentLine_first_char = ''
let g:indentLine_showFirstIndentLevel = 0
let g:indentLine_enabled = 1
let g:indentLine_fileTypeExclude = ['help', 'nerdtree', 'text', 'sh']
let g:indentLine_bufNameExclude = ['_.*', 'NERD_tree.*']
let g:indentLine_maxLines = 3000
"nnoremap \il :IndentLinesToggle


"set Raimondi/delimitMate
let delimitMate_expand_cr=1
" Syntastic
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0

let g:syntastic_cpp_compiler = 'g++'
let g:syntastic_cpp_compiler_options = "-std=c++11 -Wall -Wextra -Wpedantic"
let g:syntastic_c_compiler_options = "-std=c11 -Wall -Wextra -Wpedantic"

" vim-multiple-cursor
let g:multi_cursor_use_default_mapping=0
" Default mapping
let g:multi_cursor_next_key='<C-n>'
let g:multi_cursor_prev_key='<C-p>'
let g:multi_cursor_skip_key='<C-x>'
let g:multi_cursor_quit_key='<Esc>'

" 커서가 있는 줄을 강조함
set cursorline
" 상태바 표시를 항상한다
set laststatus=2 
set statusline=\ %<%l:%v\ [%P]%=%a\ %h%m%r\ %F\
" 검색 설정
set ignorecase
" 마지막으로 수정된 곳에 커서를 위치함
au BufReadPost *
\ if line("'\"") > 0 && line("'\"") <= line("$") |
\ exe "norm g`\"" |
\ endif
" Markdown 문법 설정 (Git 에서 사용)
augroup markdown
    " remove previous autocmds
    autocmd!
    " set every new or read *.md buffer to use the markdown filetype
    autocmd BufRead,BufNew *.md setf markdown
augroup END

set termguicolors
let g:tokyonight_style = 'storm' " available: night, storm
let g:tokyonight_enable_italic = 1
let g:tokyonight_menu_selection_background = 'red'
colorscheme tokyonight
```

## plugin 설치 방법

[참조](https://jjeaby.medium.com/vim-을-ide-처럼-사용하기-plugin-설정-87b40c5bfc14)

```powershell
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

vim을 재시동하여 :PluginInstall 실행

- PluginSearch 안될때
  - 이전에는 다른 사이트에서 사람들이 올렸었는데
  - 현재는 대부분 git을 이용하여 배포하고 있음
  - curl -v -o ~/.vim/bundle/.vundle/script-names.vim-scripts.org.json <https://raw.githubusercontent.com/i-cooltea/resource/master/vim-api_scripts.json>
  - wget <https://raw.githubusercontent.com/i-cooltea/resource/master/vim-api_scripts.json> -v -O ~/.vim/bundle/.vundle/script-names.vim-scripts.org.json
- 해당 경로의 파일로 대치해주면 플러그인 서치가 동작하는 것을 확인

[플러그인 관련 자료](https://edward0im.github.io/technology/2020/09/17/vim/)

[github](https://edward0im.github.io/technology/2020/09/17/vim/#org1b272ca)

### youcompleteme (자동완성) - UBUNTU 20.04

```powershell
apt install build-essential cmake vim-nox python3-dev
apt install mono-complete golang nodejs default-jdk npm
cd ~/.vim/bundle/YouCompleteMe
python3 install.py --all
```

[github](https://github.com/ycm-core/YouCompleteMe#linux-64-bit)

## COMMAND

- 창을 분리하여 열기

```bash
:sp + [file_name]
:sp + [ctrl] + d : 현재 폴더의 파일명 확인
```

- copy & paste

```bash
# 한줄을 복사
yy

# 복사한 줄을 붙여넣기
p
```

- 자동완성

```bash
[ctrl] + p
```

- 파일트리 출력

```bash
\nt # 플러그인 설치 후 사용할 수 있음
# 입력 없이 해당 명령어를 입력하게 되면 현재 파일 트리를 출력하여 줌
```

- 분할된 창 이동

```bash
[ctrl] + w
[ctrl] + h 
[ctrl] + j
[ctrl] + k
[ctrl] + l
```

- 드래그 하기
- 커맨드모드 상에서 v 입력 후 포인터를 이동하게 되면 선택

- 수직 분할

```bash
:vs
```

- r : 현재 커서에 있는 글자 바꾸기
- s : 현재 커서 글자 바꾸고 입력 모드
- %s/단어/new단어/gc : 단어를 변경
- ctrl + x + ctrl + l : 라인단위 지동완성 기능
- ctrl + x + ctrl + f : 파일명, 경로 자동완성.

![명령어1](./image/vim이동닽축키.jpeg)

![명령어2](./image/vim명령어단축키.jpeg)

![명령어3](./image/vim단축키2.png)

### macvim 어플리케이션 항목에 추가

```powershell
mv /usr/local/Cellar/macvim/8.2-171/MacVim.app /Applications
ln -s /Applications/MacVim.app /usr/local/Cellar/macvim/8.2-171
```

- 어플리케이션 폴더에 추가함으로서
- 동작 시, fn키 고정 기능을 활성화하기 위해
- [시스템 환경 설정] - [키보드] - [단축키] - [기능 키] 항목에 macvim을 추가하면
- 동작 시 터치 바에 펑션키가 활성화되는 것을 볼 수 있음

### makefile로 컴파일하기

- nmap <F5> : make all<CR>
- vimrc 파일에 위와 같은 명령어를 추가해놓으면 F5 키를 통해 makefile을 통해 바로 컴파일을 실행할 수 있음

## 윈도우 설정 방법

- vimrc 위치 : C:\Users\정태원
- 한글 입력 관련 :

```makefile
" 한글 입력 설정
"set encoding=utf-8  "linux
"set termencoding=utf-8 "linux
set encoding=cp949
set fileencodings=utf-8
set langmenu=cp949
```

- 윈도우에서는 utf-8이 정상 동작하지 않아서 위 코드와 같이 세팅
