.. _reference-editors-vim-mi_vimrc:

#########
Mi .vimrc
#########

Fuentes
*******

* https://github.com/spf13/spf13-vim
* https://github.com/chriskempson/tomorrow-theme/tree/master/vim/colors

------------------------

spf13-vim
*********

.. code-block:: bash

    vim ~/.vimrc.bundles.local

.. code-block:: bash

    " Guias de indentacion
    Bundle 'Yggdroot/indentLine'

.. code-block:: bash

    vim ~/.vimrc.local

.. code-block:: bash

    set mouse=
    set nospell
    set nofoldenable
    set nocursorline

    let g:indent_guides_enable_on_vim_startup = 0

    " Cambiar cursor en modo edicion en Konsole
    let &t_SI = "\<Esc>]50;CursorShape=1\x7"
    let &t_EI = "\<Esc>]50;CursorShape=0\x7"

.. code-block:: bash

    cd ~
    curl https://j.mp/spf13-vim3 -L > spf13-vim.sh && sh spf13-vim.sh

Para actualizar

.. code-block:: bash

    cd $HOME/to/spf13-vim/
    git pull
    vim +BundleInstall! +BundleClean +q

Personalizada
*************

Esta no es tan completa como spf13, pero ya me vale.

Crear carpeta **si no existe**

.. code-block:: bash

    mkdir -p ~/.vim/colors

Dentro de ``colors`` le pongo el theme
`chriskempson/tomorrow-theme <https://github.com/chriskempson/tomorrow-theme/tree/master/vim/colors>`_


.. code-block:: bash

    " Sample .vimrc file by Martin Brochhaus
    " Presented at PyCon APAC 2012

    " ============================================
    " Note to myself:
    " DO NOT USE <C-z> FOR SAVING WHEN PRESENTING!
    " ============================================

    " Automatic reloading of .vimrc
    "" autocmd! bufwritepost .vimrc source %

    " Better copy & paste
    " When you want to paste large blocks of code into vim, press F12 before you
    " paste. At the bottom you should see ``-- INSERT (paste) --``.

    set pastetoggle=<F12>
    set clipboard=unnamed

    " Mouse and backspace
    set bs=2     " make backspace behave like normal again

    " Rebind <Leader> key
    " I like to have it here becuase it is easier to reach than the default and
    " it is next to ``m`` and ``n`` which I use for navigating between tabs.
    let mapleader = ","

    " Bind nohl
    " Removes highlight of your last search
    " ``<C>`` stands for ``CTRL`` and therefore ``<C-n>`` stands for ``CTRL+n``
    noremap <C-n> :nohl<CR>
    vnoremap <C-n> :nohl<CR>
    inoremap <C-n> :nohl<CR>

    " Quicksave command
    noremap <C-Z> :update<CR>
    vnoremap <C-Z> <C-C>:update<CR>
    inoremap <C-Z> <C-O>:update<CR>

    " bind Ctrl+<movement> keys to move around the windows, instead of using Ctrl+w + <movement>
    " Every unnecessary keystroke that can be saved is good for your health :)
    "" map <c-j> <c-w>j
    "" map <c-k> <c-w>k
    "" map <c-l> <c-w>l
    "" map <c-h> <c-w>h

    " easier moving between tabs
    map <Leader>n <esc>:tabprevious<CR>
    map <Leader>m <esc>:tabnext<CR>

    " Enable syntax highlighting
    " You need to reload this file for the change to apply
    filetype off
    filetype plugin indent on
    syntax on

    " Color scheme
    set background=dark
    set t_Co=256
    colorscheme Tomorrow-Night-Bright

    " Showing line numbers and length
    set number  " show line numbers
    set tw=79   " width of document (used by gd)
    set nowrap  " don't automatically wrap on load
    set fo-=t   " don't automatically wrap text when typing
    set colorcolumn=80
    highlight ColorColumn ctermbg=233

    " Useful settings
    set history=700
    set undolevels=700

    " Real programmers don't use TABs but spaces
    set tabstop=4
    set softtabstop=4
    set shiftwidth=4
    set shiftround
    set expandtab

    " Make search case insensitive
    set hlsearch
    set incsearch
    set ignorecase
    set smartcase

    " Disable stupid backup and swap files - they trigger too many events
    " for file system watchers
    set nobackup
    set nowritebackup
    set noswapfile

     " Stupid shift key fixes
    command! -bang -nargs=* -complete=file E e<bang> <args>
    command! -bang -nargs=* -complete=file W w<bang> <args>
    command! -bang -nargs=* -complete=file Wq wq<bang> <args>
    command! -bang -nargs=* -complete=file WQ wq<bang> <args>
    command! -bang Wa wa<bang>
    command! -bang WA wa<bang>
    command! -bang Q q<bang>
    command! -bang QA qa<bang>
    command! -bang Qa qa<bang>
