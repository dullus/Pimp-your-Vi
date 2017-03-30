# Command Line Hacks

3. **[VI](#h3)**  
    3.1 [pimp your VIM](#h3-1)

# <a name="h3"></a>3. VI
## <a name="h3-1"></a>3.1 pimp your VIM

1. set some variables in `.vimrc`
```shell
syntax on
filetype plugin indent on
set number
set laststatus=2
```

2. install plugin manager <a href="https://github.com/tpope/vim-pathogen">Pathogen</a>
```shell
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```

  add to `.vimrc`
```shell
execute pathogen#infect()
```

3. install <a href="https://github.com/vim-airline/vim-airline">VIM Airline</a> status bar, themes and other plugins
```shell
cd ~/.vim/bundle/
# airline
git clone https://github.com/vim-airline/vim-airline
# fuGITive
git clone https://github.com/tpope/vim-fugitive.git
vim -u NONE -c "helptags vim-fugitive/doc" -c q
# gitgutter
git clone https://github.com/airblade/vim-gitgutter.git
# JS support
git clone https://github.com/pangloss/vim-javascript.git
# theme
git clone https://github.com/albertorestifo/github.vim.git
```
generate helptags in VI by `:Helptags`

4. better cursorline highlighted
```
:hi CursorLine cterm=NONE ctermbg=yellow ctermfg=black
```


### <a name=""></a>3.1.1 Final `.vimrc`
```
execute pathogen#infect()
set t_Co=256
syntax on
filetype plugin indent on
set number
set laststatus=2
set cursorline
autocmd InsertEnter * highlight CursorLine cterm=NONE ctermbg=yellow ctermfg=black
autocmd InsertEnter * highlight CursorLineNR ctermfg=black
let g:gitgutter_sign_modified = '•'
let g:gitgutter_sign_added = '❖'
highlight GitGutterAdd guifg = '#A3E28B'
let g:gitgutter_enabled = 1
colorscheme github
let g:airline_theme='github'
set modelines=0
set nocompatible
set backspace=2
```
<hr/>
