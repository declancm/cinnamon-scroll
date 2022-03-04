# Cinnamon Scroll

Smooth scrolling for any vertical movement command.

It is highly customizable, supports using '.' (single repeat) as it doesn't break\
or replace your last performed command, and even supports scrolling over folds.

Fun bonus: supports tpope's vim-repeat if that's your jam.

## Installation

Install with your favorite package manager. No configuration is required to get\
started with the default keymaps.

Install 'tpope/vim-repeat' to use the '.' command to repeat scroll movements.\
Totally optional though :D.

### Vim-Plug

```vim
Plug "tpope/vim-repeat" " optional
Plug "declancm/vim-cinnamon"
```

## The Command

```vim
<Cmd>Cinnamon arg1 arg2 arg3 arg4 arg5 arg6 <CR>
```

_Note: A whitespace is used to separate the arguments._

* arg1 = The movement command (eg. 'gg'). This argument is required as there's\
  no default value.
* arg2 = Keep cursor centered in the window. (1 for on, 0 for off). Default is 1.
* arg3 = Accept a count before the command (1 for on, 0 for off). Default is 0.
* arg4 = Length of delay between lines (in ms). Default is 5.
* arg5 = Slowdown at the end of the movement (1 for on, 0 for off). Default is 1.
* arg6 = Max number of lines before scrolling is skipped. Mainly just for big\
  commands such as 'gg' and 'G'. Default is 150.

## Default Keymaps

```vim
" Paragraph movements.
nnoremap <silent> { <Cmd>Cinnamon { 0 <CR>
nnoremap <silent> } <Cmd>Cinnamon } 0 <CR>
xnoremap <silent> { <Cmd>Cinnamon { 0 <CR>
xnoremap <silent> } <Cmd>Cinnamon } 0 <CR>

" Half-window movements.
noremap <silent> <C-u> <Cmd>Cinnamon <C-u> <CR>
noremap <silent> <C-d> <Cmd>Cinnamon <C-d> <CR>
inoremap <silent> <C-u> <Cmd>Cinnamon <C-u> <CR>
inoremap <silent> <C-d> <Cmd>Cinnamon <C-d> <CR>

" Page movements.
nnoremap <silent> <C-b> <Cmd>Cinnamon <C-b> 1 1 <CR>
nnoremap <silent> <C-f> <Cmd>Cinnamon <C-f> 1 1 <CR>
nnoremap <silent> <PageUp> <Cmd>Cinnamon <C-b> 1 1 <CR>
nnoremap <silent> <PageDown> <Cmd>Cinnamon <C-f> 1 1 <CR>
```

To **disable** the default keymaps, add the following to your .vimrc:

```vim
let g:cinnamon_no_defaults = 1
```

## Extra Keymaps

```vim
" Start and end of file movements.
nnoremap <silent> gg <Cmd>Cinnamon gg 0 0 3 <CR>
nnoremap <silent> G <Cmd>Cinnamon G 0 0 3 <CR>
xnoremap <silent> gg <Cmd>Cinnamon gg 0 0 3 <CR>
xnoremap <silent> G <Cmd>Cinnamon G 0 0 3 <CR>

" Previous/next cursor position.
nnoremap <silent> <C-o> <Cmd>Cinnamon <C-o> 0 0 3 <CR>
nnoremap <silent> <C-i> <Cmd>Cinnamon <C-i> 0 0 3 <CR>

" Previous/next search result.
nnoremap <silent> n <Cmd>Cinnamon n 0 0 3 <CR>
nnoremap <silent> N <Cmd>Cinnamon N 0 0 3 <CR>
nnoremap <silent> * <Cmd>Cinnamon * 0 0 3 <CR>
nnoremap <silent> # <Cmd>Cinnamon # 0 0 3 <CR>

" Up and down movements which accepts a count (eg. 69j to scroll down 69 lines).
nnoremap <silent> k <Cmd>Cinnamon k 0 1 2 0 <CR>
nnoremap <silent> j <Cmd>Cinnamon j 0 1 2 0 <CR>
nnoremap <silent> <Up> <Cmd>Cinnamon k 0 1 2 0 <CR>
nnoremap <silent> <Down> <Cmd>Cinnamon j 0 1 2 0 <CR>
xnoremap <silent> k <Cmd>Cinnamon k 0 1 2 0 <CR>
xnoremap <silent> j <Cmd>Cinnamon j 0 1 2 0 <CR>
xnoremap <silent> <Up> <Cmd>Cinnamon k 0 1 2 0 <CR>
xnoremap <silent> <Down> <Cmd>Cinnamon j 0 1 2 0 <CR>
```

To **enable** the extra keymaps, add the following to your .vimrc:

```vim
let g:cinnamon_extras = 1
```

## Creating Custom Keymaps

Custom keymaps can be created using the 'Cinnamon' command.

```vim
" Disable default keymaps
let g:cinnamon_no_defaults = 1
" Jump to first/last line of paragraph intead of the whitespace
xnoremap <silent> { k<Cmd>Cinnamon {j 0 <CR>
xnoremap <silent> } j<Cmd>Cinnamon }k 0 <CR>
```

The first argument for the '{' keymap will perform a movement of '{j' which will\
jump to the first whitespace line and then move one line down. The next argument\
disables the window scrolling as the default is on.
