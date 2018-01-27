# My Favorite Commands from a Year of Vim

_Captured: 2017-10-19 at 20:03 from [spin.atomicobject.com](https://spin.atomicobject.com/2017/09/24/favorite-vim-commands/)_

I've been using [Vim](http://www.vim.org) as as my primary text editor for a little over a year now, and I'd like to share some of my favorite commands that I've discovered during that time. I'll focus on sharing commands over configuration, so they can be used in any Vim environment.

## Movement Commands

### `t_` | `T_`

`t` will move you to the next occurrence of the character afterwards, placing your cursor right before the character searched. `T` is very similar, except it will move backwards to the next occurrence, placing your cursor to the right of the character searched.

### `f_` | `F_`

The `f` command is very similar to the `t` command, but it places your cursor on top of the character. The `F` command works how you might expect, moving your cursor backwards and on top of the next occurrence of the selected character.

### `;`

The `;` command is very helpful, allowing you to repeat your last `f` or `t` command.

### `gg` | `G`

These commands let you move around the entire file. `gg` will move you to the first line in the file, and `G` will move you to the last line in the file. Alternatively, if you type `nG` where `n` is a number, you'll jump to that to that line.

### `*` | `#`

The `*` command will search forward for the word under your cursor, while the `#` command will search backwards. These two are useful for jumping around a file to find a local function or variable.

## Indentation Commands

### `<` | `>` | `=`

These commands are all related to indentation. `<` and `>` will increase or decrease indentation respectively. The `=` command is similar except that Vim sets the indentation to what it thinks it should be, given the lines contextually. All of these commands can be applied to just the current line by repeating them twice, instead of combining them with a movement.

`gg=G`  
This is a handy command that will tell Vim to redo the indentation on your current buffer.

## Moving Text to/from System Clipboard

After using Vim for a little while, you might wonder how to get the text from your clipboard into Vim, and vice versa.

Vim's command to access any registers is `"`. After that, you can use `+` to access the system clipboard register. Therefore, `"+p` would be the equivalent of a paste command, and `"+y` would be the equivalent of a copy command (if you're in visual mode or you use some movement with the `y` command).

## Text Objects

Many Vim commands can be applied to text objects instead of movements, and they often allow for much easier text manipulation. A few text objects and their corresponding Vim keys are **w**ord, **t**ag, **p**aragraph, **s**entence, and others like parentheses, quotes, and the varieties of brackets.

One example of how to work with these text objects is `diw`. I read this command as **d**elete **i**nside **w**ord. The effect is to delete the current word from anywhere within it. Instead of **i**, you can use **a**, which will include the surrounding whitespace in the text object.

## Visual Selections

I think most Vim users know about the `v` command to enter visual selection mode. As you might expect, this mode lets you select the lines between the starting point and your cursor, wrapping the selection across any line breaks encountered.

There are two other modes to visual selection: line selection and block selection. Line selection is entered with `V`, allowing you to select entire lines at a time. Block selection, which you can enter with `cmd-v`, will select a rectangular area from your starting cursor to your end cursor. This allows you to insert the same text on multiple lines or replace parts of content on multiple lines.

What commands do you find most useful? I'd love to hear about them in the comments.
