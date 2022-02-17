# cinnamon-scrolls

A scrolling plugin for vim that works with any movement command.

It is highly customizable, works with any movement and even supports scrolling\
over folds.

## Installation

Install with your favorite package manager.

### Vim-Plug

```vim
Plug "declancm/git-scripts-vim"
```

### Packer

```lua
use "declancm/git-scripts-vim"
```

_Note: Packer is a package manager for neovim._

## The Command

```vim
<Cmd>Scroll arg1 arg2 arg3 arg4 arg5 <CR>
```

* arg1 = Movement command (eg. 'gg'). This argument is required as there's no\
  default value.
* arg2 = Scroll the window (1 for on, 0 for off). Default is 1.
* arg3 = Accept a count before the command (1 for on, 0 for off). Default is 0.
* arg4 = Length of delay between lines (in ms). Default is 5.
* arg5 = Slowdown at the end of the movement (1 for on, 0 for off). Default is 1.

Custom keymaps can be created using the 'Scroll' command. Look at the Default\
Keymaps for examples on how to use it.

## Default Keymaps

```vim
" Paragraph movements
nnoremap <silent> { <Cmd>Scroll { 0 <CR>
nnoremap <silent> } <Cmd>Scroll } 0 <CR>
xnoremap <silent> { k<Cmd>Scroll {j 0 <CR>
xnoremap <silent> } j<Cmd>Scroll }k 0 <CR>
" In visual mode, the paragraph stops at the first/last line of the paragraph
" instead of the whitespace for better highlighting.

" Half-window movements
nnoremap <silent> <C-u> <Cmd>Scroll <C-u> <CR>
nnoremap <silent> <C-d> <Cmd>Scroll <C-d> <CR>
inoremap <silent> <C-u> <Cmd>Scroll <C-u> <CR>
inoremap <silent> <C-d> <Cmd>Scroll <C-d> <CR>

" Page movements
nnoremap <silent> <C-b> <Cmd>Scroll <C-b> <CR>
nnoremap <silent> <C-f> <Cmd>Scroll <C-f> <CR>
inoremap <silent> <C-b> <Cmd>Scroll <C-b> <CR>
inoremap <silent> <C-f> <Cmd>Scroll <C-f> <CR>
nnoremap <silent> <PageUp> <Cmd>Scroll <C-b> <CR>
nnoremap <silent> <PageDown> <Cmd>Scroll <C-f> <CR>
inoremap <silent> <PageUp> <Cmd>Scroll <C-b> <CR>
inoremap <silent> <PageDown> <Cmd>Scroll <C-f> <CR>
```

To **disable** the default keymaps, add the following to your .vimrc:

```vim
let g:cinnamon_no_defaults = 1
```

## Extra Keymaps

```vim
" Start and end of file movements
nnoremap <silent> gg <Cmd>Scroll gg 0 0 1 <CR>
nnoremap <silent> G <Cmd>Scroll G 0 0 1 <CR>
xnoremap <silent> gg <Cmd>Scroll gg 0 0 1 <CR>
xnoremap <silent> G <Cmd>Scroll G 0 0 1 <CR>

" Up and down movements which accepts a count (eg. 69j to scroll down 69 lines)
nnoremap <silent> k <Cmd>Scroll k 0 1 2 0 <CR>
nnoremap <silent> j <Cmd>Scroll j 0 1 2 0 <CR>
nnoremap <silent> <Up> <Cmd>Scroll k 0 1 2 0 <CR>
nnoremap <silent> <Down> <Cmd>Scroll j 0 1 2 0 <CR>
xnoremap <silent> k <Cmd>Scroll k 0 1 2 0 <CR>
xnoremap <silent> j <Cmd>Scroll j 0 1 2 0 <CR>
xnoremap <silent> <Up> <Cmd>Scroll k 0 1 2 0 <CR>
xnoremap <silent> <Down> <Cmd>Scroll j 0 1 2 0 <CR>
```

To **enable** the extra keymaps, add the following to your .vimrc:

```vim
let g:cinnamon_extras = 1
```
