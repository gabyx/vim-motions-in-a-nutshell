<p align="center">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Neovim-mark.svg/1200px-Neovim-mark.svg.png" width="100px">
</p>

# Vim Motions in a Nutshell

**What you _really_ need to know when starting to learn Vim motions.**

## Motivation

Vim motions are awesome and work almost everywhere. I share here an extract and
condensed version of what the most important commands are to get you productive
as fast a possible. This document is not here to teach you all of Vim's magic
(because I don't know them too =)) but rather to present you the 10-20 most
valuable commands which made my journey in Vim a steep learning curve. From this
basics presented in this document you can start exploring more and more and
refine your habits with even more awesomeness.

**Start with as few as possible, but be effective at the same time.**

# Preliminaries

You can use VS Code with a Vim extension or better `neovim` to follow the below
summary. Many text based softwares have a vim-mode, or plugins.

## Cancel Anything

<kbd>Ctrl</kbd>+<kbd>c</kbd> **or** <kbd>Esc</kbd>

Gets you into `Normal` mode from anywhere. Press this when you entered wrong
command sequences or other mistakes. 

> [!TIP]
> Remap <kbd>Caps Lock</kbd> to
> <kbd>Ctrl</kbd> or <kbd>Esc</kbd> to ease finger strain. You can do this with:
>
> - MacOS: In System Settings (Keyboard -> Modifiers Keys) or with
> [Karabiner-Elements](https://karabiner-elements.pqrs.org/).
>
> - Windows: [PowerToys](https://learn.microsoft.com/de-de/windows/powertoys/) or
> [dual-key-remap](https://github.com/ililim/dual-key-remap).


---

## Undo/Redo

Go to normal mode (see above) and press <kbd>u</kbd> to undo the last action. To
redo press <kbd>Ctrl</kbd>+<kbd>r</kbd>.

---

## Normal Mode and Visual Mode

Vim is a modal editor. It has three important modes:
- `Normal` : jump around and use keybindings (default).
- `Insert` : write text. 
- `Visual` : select lines/blocks of text 

You can switch any mode from the normal mode using the following keys:
- <kbd>i</kbd>/<kbd>a</kbd> : `Insert`
- <kbd>v</kbd> : `Visual` mode (normal selection).
- <kbd>Shift</kbd> + <kbd>v</kbd> : `Line Visual` mode (line selections).
- <kbd>Ctrl</kbd> + <kbd>v</kbd> : `Block Visual` mode (block selections).

## Entering Command Mode

In normal mode, you can press <kbd>:</kbd> to enter `Command` mode. You
won't use this much at the beginning. If you accidentally end up in `Command` mode, press
<kbd>Esc</kbd> or <kbd>Ctrl</kbd>+<kbd>c</kbd> to go back into `Normal` mode.

---

## Move the Cursor Around

To move your cursor in the buffer you have to learn the following keys. This
takes some time but you will memorize them after 2-3 days.

- <kbd>h</kbd> and <kbd>l</kbd> : Moves one character to the left/right in the
  current buffer.
- <kbd>j</kbd> and <kbd>k</kbd> : Moves line down/up in the current buffer.

Lots CLI tools etc. also use these mappings and its best to stick to them. It is also more efficient as they keep your fingers on the [home row](https://simple.wikipedia.org/wiki/Home_row).

> [!NOTE]
> To battle squeeze these mappings into your mechanical cortex I
recommend [ThePrimagean's](https://github.com/ThePrimeagen/vim-be-good) plugin
game in `nvim` to quickly memorize or play
[this game](https://vim-adventures.com).

---

## Insert at Beginning or End

The next most important command is to insert at the beginning (skipped white
space) or the end with

- <kbd>I</kbd> : Insert at the beginning of the line.
- <kbd>A</kbd> : Insert at the end of the line (append).

---

## Move the Cursor Faster

To move faster on a line you should memorize:

- <kbd>w</kbd> or <kbd>b</kbd> : Jump to the next/previous starting word.

- <kbd>W</kbd> and <kbd>B</kbd> : Jump to the next/previous starting word (with
  punctuation).

- <kbd>Ctrl</kbd>+<kbd>d</kbd> and <kbd>Ctrl</kbd>+<kbd>u</kbd>: Move cursor
  down/up 1/2 page.

---

## Copy/Delete Lines

Copy (yank) and delete are vim _operators_: they change text objects.

Doubling the operator key applies it to the line (a text object).

- <kbd>y</kbd><kbd>y</kbd> : Copy the current line.
- <kbd>d</kbd><kbd>d</kbd> : Delete the current line.

---

## Pasting

- <kbd>p</kbd> : Paste the clipboard after the cursor.
- <kbd>P</kbd> : Paste the clipboard before the cursor.

---

## Insert/Append

- <kbd>o</kbd> : Insert on a new line below the current one.
- <kbd>O</kbd> : Insert on a new line above the current one.

---

## Delete/Substitute Characters

This command seems useless since you have <kbd>Backspace</kbd>, however
correcting small mistakes is easier like this because you will move around with
your cursor in `Normal` mode and then when pressing <kbd>x</kbd> or <kbd>s</kbd>
will directly delete/substitute the current character:

- <kbd>x</kbd> : Delete the current character in `Normal` mode or the selection
  in `Visual` mode.
- <kbd>s</kbd> : Substitute the current character in `Normal` mode or the
  selection in `Visual` mode.

---

## Select Lines or Blocks

To select lines go to `Visual` mode with <kbd>v</kbd> or `Block Visual` mode
with <kbd>Ctrl</kbd>+<kbd>v</kbd>. When the selection has been done, you can
copy/delete or change/substitute it with the commands already learned.

---

## vim motion syntax

This is where the fun truly begins!
vim allows to combine motions and operators to form "sentences".
Sentences have the following structure:

```
[count]<operator>[count]<motion>`
```

For example to _delete two words_: `d2w`

> [!NOTE]
> The first count in the structure above is used to run the whole sentence multiple times
>
> Learn more about the syntax: [1](https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/editing-like-magic-with-vim-operators/), [2](https://agill.xyz/vim/motions)

---

## Change Inside/Around Stuff

"Below" are some other useful sentences you want to remember:

**Change Inside/Around**:

- <kbd>ca"</kbd> : Change (<kbd>c</kbd>) _around_ quotes `"` found from the
  current cursor position.
- <kbd>ca"</kbd> : Change (<kbd>c</kbd>) _inside_ quotes `"` found from the
  current cursor position.

**Yank Inside/Around**:

- <kbd>ya"</kbd> : Copy (<kbd>y</kbd>) _around_ quotes `"` found from the
  current cursor position.
- <kbd>yi"</kbd> : Copy (<kbd>y</kbd>) _inside_ quotes `"` found from the
  current cursor position.

**Delete Inside/Around**:

- <kbd>da"</kbd> : Delete _around_ quotes `"` found from the current cursor
  position.
- <kbd>di"</kbd> : Delete _inside_ quotes `"` found from the current cursor
  position.

**Copy/Delete/Change till Character**:

- <kbd>ct?</kbd> : Change the text selection till the next character `?`.
- <kbd>yt?</kbd> : Copy the text selection till the next character `?`.
- <kbd>dT?</kbd> : Delete the text selection till the previous character `?`.

**Copy/Delete/Change Till End**:

- <kbd>c$</kbd> : Change till end of line.
- <kbd>c0</kbd> : Change till beginning of line.
- <kbd>y$</kbd> : Yank till end of line.
- <kbd>y0</kbd> : Yank till beginning of line.
- <kbd>d$</kbd> : Delete till end of line.
- <kbd>d0</kbd> : Delete till beginning of line.

**Note:** Yeah, you guessed it, you can use also other things in place of `"`.
Try to use <kbd>(</kbd> or <kbd>[</kbd> or <kbd>{</kbd> or <kbd>`</kbd> or
<kbd>'</kbd> etc. to easily change around/inside this characters. Also you can
use <kbd>w</kbd> to do the action inside/around a word.

## Miscellaneous

- <kbd>&gt;</kbd><kbd>&gt;</kbd> : Add indentation on the current line.
- <kbd>&lt;</kbd><kbd>&lt;</kbd> : Remove indentation on the current line.
- <kbd>=</kbd><kbd>=</kbd> : Format current line.

In `Block Visual` mode: Select some lines, then use

- <kbd>I</kbd> : Insert on all lines. Once done, press <kbd>Esc</kbd> to make it
  apply on all lines.
- <kbd>C</kbd> : Change the selection on all lines. Once done, press
  <kbd>Esc</kbd> to make it apply on all lines.

## Jumping around

Vim keeps a list of your jumps within or between buffers.
You can jump back and forth in you jump history with <kbd>Ctrl</kbd>+<kbd>i</kbd>/<kbd>Ctrl</kbd>+<kbd>o</kbd>.

When programming, this is very useful in conjunction with `gd` (go to definition == <kbd>Ctrl</kbd>+<kbd>click</kbd> in VSCode)

## The End

That's basically it and are the top commands I use daily. There is obviously
much more on the Vim motions side. Now, start practicing it, once learned you
will not change using it, trust me. =)


---

## Downsides

- IDE setup is complicated
- keybindings logic not 100% consistent

Some editors aim to address these aspects:
- https://helix-editor.com
- http://kakoune.org


