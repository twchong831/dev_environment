# Vim to flutter setting progress

- using neovim

## plugin

[plugin 1](https://github.com/dart-lang/dart-vim-plugin)

```bash
# plugin install

call plug#begin()
"... <snip other plugins>
Plug 'dart-lang/dart-vim-plugin'

call plug#end()
```

- vim에서 flutter를 사용하기 위한 coc 플러그인 설치

[flutter snippet](https://github.com/neoclide/coc-snippets)

```vim
:CocInstall coc-flutter
:CocInstall coc-flutter-tools
:checkhealth
```

### error

#### python

1. python 동작 확인

    ```Bash
    :pyx print('hello')    # not active
    :checkhealth provider
    ```

2. 동작이 제대로 안되는 경우 checkhealth provider로 연결성 확인

    ```Bash
    # error
    ## Node.js provider (optional)
     - INFO: Node.js: v19.8.1
     - WARNING: Missing "neovim" npm (or yarn, pnpm) package.
        - ADVICE:
          - Run in shell: npm install -g neovim
          - Run in shell (if you use yarn): yarn global add neovim
          - Run in shell (if you use pnpm): pnpm install -g neovim
          - You may disable this provider (and warning) by adding `let g:loaded_node_provider = 0` to your init.vim

    ## Perl provider (optional)
     - WARNING: "Neovim::Ext" cpan module is not installed
        - ADVICE:
          - See :help |provider-perl| for more information.
          - You may disable this provider (and warning) by adding `let g:loaded_perl_provider = 0` to your init.vim
    ```

3. 에러 항목을 확인하고 재설치 수행
4. init.vim 세팅

    ```bash
    sudo gem install neovim
    npm install -g neovim
    ```

5. 에러 항목 재 확인

    ```bash
    :checkhealth provider
    ```

   - 결과 확인

    ```bash
    provider: health#provider#check
    ========================================================================
    ## Clipboard (optional)
     - OK: Clipboard tool found: pbcopy
    
    ## Python 3 provider (optional)
     - INFO: `g:python3_host_prog` is not set.  Searching for python3 in the     environment.
     - INFO: Multiple python3 executables found.  Set `g:python3_host_prog` to avoid     surprises.
     - INFO: Executable: /opt/homebrew/anaconda3/bin/python3
     - INFO: Other python executable: /usr/bin/python3
     - INFO: Other python executable: /opt/homebrew/bin/python3
     - INFO: Python version: 3.9.13
     - INFO: pynvim version: 0.4.3
     - OK: Latest pynvim is installed.

    ## Python virtualenv
     - OK: no $VIRTUAL_ENV

    ## Ruby provider (optional)
     - INFO: Ruby: ruby 2.6.10p210 (2022-04-12 revision 67958) [universal.arm64e-darwin22]
     - INFO: Host: /usr/local/bin/neovim-ruby-host
     - OK: Latest "neovim" gem is installed: 0.9.0

    ## Node.js provider (optional)
     - INFO: Node.js: v19.8.1
     - INFO: Nvim node.js host: /opt/homebrew/lib/node_modules/neovim/bin/cli.js
     - OK: Latest "neovim" npm/yarn/pnpm package is installed: 4.10.1

    ## Perl provider (optional)
     - WARNING: "Neovim::Ext" cpan module is not installed
        - ADVICE:
          - See :help |provider-perl| for more information.
          - You may disable this provider (and warning) by adding `let g:loaded_perl_provider = 0` to your init.vim
    ```

    - 수정사항 실행

    ```bash
    brew install cpanminus
    sudo cpanm -n Neovim::Ext
    # error...
    
    brew install perl
    ```

...안되고 잇음...
