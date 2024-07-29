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
summary.

## Cancel Anything

<kbd>Ctrl</kbd>+<kbd>c</kbd> **or** <kbd>Esc</kbd>

Gets you into `Normal` mode form anywhere. Press this when you entered wrong
command sequences or other mistakes. This will be probably your most pressed
command at beginning. Don't be daunted, it will get less.

Also its highly recommended you improve your <kbd>Esc</kbd> or
<kbd>Ctrl</kbd>+<kbd>C</kbd> key presses by remapping <kbd>Caps Lock</kbd> to
<kbd>Ctrl</kbd> or <kbd>Esc</kbd>. You can do this with:

- MacOS: In System Settings (Keyboard -> Modifiers Keys) or with
  [Karabiner-Elements](https://karabiner-elements.pqrs.org/).

- Windows: [PowerToys](https://learn.microsoft.com/de-de/windows/powertoys/) or
  [dual-key-remap](https://github.com/ililim/dual-key-remap).

---

## Undo/Redo

Go to normal mode (see above) and press <kbd>u</kbd> to undo the last action. To
redo press <kbd>Ctrl</kbd>+<kbd>r</kbd>.

---

## Normal Mode and Visual Mode

Vim has three important modes, `Normal`, `Insert` and `Visual` mode. `Normal`
mode is mostly where you move the cursor around and jump around in your
document. The `Visual` mode is to select lines/blocks etc. and to do actions on
them. `Insert` mode is to write text. To go to `normal` mode you use
<kbd>Ctrl</kbd>+<kbd>c</kbd> or <kbd>Esc</kbd> as described above. To go to
insert press <kbd>i</kbd> and for `Visual` mode press:

- <kbd>v</kbd> : `Visual` mode (normal selection).
- <kbd>V</kbd> : `Line Visual` mode (line selections).
- <kbd>Ctrl</kbd> + <kbd>v</kbd> for the `Block Visual` mode (block selections).

## Entering Command Mode

When you (accidentally) press <kbd>:</kbd>, you will enter `Command` mode. You
won't use this much at the beginning. If you end up in `Command` mode, press
<kbd>Esc</kbd> or <kbd>Ctrl</kbd>+<kbd>c</kbd> to go back into `Normal` mode.

---

## Move the Cursor Around

To move your cursor in the buffer you have to learn the following keys. This
takes some time but you will memorize them after 2-3 days.

- <kbd>h</kbd> and <kbd>l</kbd> : Moves one character to the right/left in the
  current buffer.
- <kbd>j</kbd> and <kbd>k</kbd> : Moves line up/down in the current buffer.

The point of not remapping these keys is, that you will want this experience
since lots CLI tools etc. also use these mappings and its best to stick to them.

**Note**: To battle squeeze these mappings into your mechanical cortex I
recommend [ThePrimagean's](https://github.com/ThePrimeagen/vim-be-good) plugin
game in `nvim` to quickly memorize or play
[this game](https://vim-adventures.com).

---

## Insert at the Beginning or End

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

- <kbd>y</kbd> : Copy the current line.
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

## Change Inside/Around Stuff

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
- <kbd>dt?</kbd> : Delete the text selection till the next character `?`.

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

## The End

That's basically it and are the top commands I use daily. There is obviously
much more on the Vim motions side. Now, start practicing it, once learned you
will not change using it, trust me. =)
