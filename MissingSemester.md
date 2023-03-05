# Missing Semester MIT Course

## Navigating Shell
`cd ~` --> home directory\
`which node` --> shows you the file path it’s coming from \
`echo $PATH` --> shows you all paths which will be searched\
`cd -` --> will go to the previous directory\
`Ls -l` --> lists will a long list\
`mv` --> will rename and or move a file\
`cp` --> will copy a file\
`man ls` --> give a manual for that program\
`cat` --> will print the contents of a file\
iostreams are available in shells < / > / >>\
`#` --> means running as root\
`$` --> running as user\
`Sudo su` --> will open terminal as root user\
`Echo 1 | sudo tee brightness`\
'open' --> will open files\

## Scripting a Shell
`source mcd.sh` --> will define a function in your shell
`mcd test` is now possible from source mcd.sh
`!!` runs last command
`False ; echo “Cha”` concatenates commands into the same line
`foo=$(pwd)` will interpolate
`echo “Starting program at $(date) within $(pwd)”`
`$0` is name of program, `$#` number of args, `$$` is process id, `$@` similar to spread and will open all arguments
`grep` is a program for searching for strings, 
`$?` gives most recent exit status

`
for file in "$@ ; do
    grep foobar "$file" > /dev/null 2> /dev/null
    # When pattern is not found, grep has exit status 1
    # We redirect STDOUT and STDERR to a null register since we do not care about them
    if [[ $? -ne 0 ]]; then #use [[ for bash conditionals ]]
        echo "File $file does not have any foobar, adding one"
        echo "# foobar" >> "$file"
    fi
done
`

`ls *.sh` regex can work here
`ls project?` Will check only a single wildcharacter after

`Convert image.png image.jpg` OR `convert image.{png, jpg}`

`Touch foo{1, 2, 3}`
`Cp project{1,2}`
`Touch project{1,2}/src/test/test/{1,2,3}.py`
`Touch {foo, bar}/{a..j}`
`Diff <(ls foo) <(ls bar) this will check for diffs begin the foo/bar folder`

Shebang —> `#! /usr/local/bin/python` OR `#! /user/bin/env python`

`shellcheck mcd.sh` —> this will give you basically intellisense
`find` command will search dir/file names

`find . -name “*.tmp” -exec rm {} \;`

`grep foobar “*.js”` —> searches for foobar within grep files
`rg` is shortened for ripgrep, same as grep but with colors

`history` will show you a history of commands you’ve ran 

`ctrl+r` will backwards search your commands
`fzf` is a tool that will fuzzy find this can be tied to `ctrl+r`, and won’t require regex like grep

`ls -R` will list sub directory structure as well
`open -a “Google Chrome” http://localhost:4000`

Functions are executed in the current shell environment whereas scripts execute in their own process. Thus, functions can modify environment variables, e.g. change your current directory, whereas scripts can’t. Scripts will be passed by value environment variables that have been exported using export

## VIM
normal mode —> `esc key`
insert mode —> `i key`
replace mode -> `r key`
Visual mode -> `v key`
CLI mode -> `:`

`:q` quit (close window)
`:w` save (“write”)
`:wq` save and quit
`:e` {name of file} open file for editing
`:ls` show open buffers
`:help` {topic} open help
`:help :w` opens help for the :w command
`:help w` opens help for the w movement

Basic movement: `hjkl` (left, down, up, right)
Words: `w` (next word), `b` (beginning of word), `e` (end of word)
Lines: `0` (beginning of line), `^` (first non-blank character), `$` (end of line)
Screen: `H` (top of screen), `M` (middle of screen), `L` (bottom of screen)
Scroll: `Ctrl-u` (up), `Ctrl-d` (down)
File: `gg` (beginning of file), `G` (end of file)
Line numbers: `:{number}<CR>` or `{number}G (line {number})`
Misc: `%` (corresponding item)
Find: `f{character}`, `t{character}`, `F{character}`, `T{character}`
find/to forward/backward {character} on the current line
, / ; for navigating matches
Search: `/{regex}`, `n` / `N` for navigating matches

Visual: `v`
Visual Line: `V`
Visual Block: `Ctrl-v`

`i` enter Insert mode
but for manipulating/deleting text, want to use something more than backspace
`o` / `O` insert line below / above
`d{motion}` delete {motion}
e.g. `dw` is delete word, `d$` is delete to end of line, `d0` is delete to beginning of line
`c{motion}` change {motion}
e.g. `cw` is change word
like `d{motion}` followed by `i`
`x` delete character (equal do `dl`)
`s` substitute character (equal to `cl`)
Visual mode + manipulation
select text, `d` to delete it or `c` to change it
`u` to undo, \<C-r> to redo
`y` to copy / “yank” (some other commands like d also copy)
`p` to paste
Lots more to learn: e.g. ~ flips the case of a character

`3w` move 3 words forward
`5j` move 5 lines down
`7dw` delete 7 words

`ci`( change the contents inside the current pair of parentheses
ci[ change the contents inside the current pair of square brackets
`da'` delete a single-quoted string, including the surrounding single quotes

Vim is customized through a plain-text configuration file in `~/.vimrc`

Search and replace

`:s` (substitute) command (documentation).

`%s/foo/bar/g`
replace foo with bar globally in file
`%s/\[.*\](\(.*\))/\1/g`
replace named Markdown links with plain URLs
Multiple windows

`:sp` / `:vsp` to split windows
Can have multiple views of the same buffer.

## RegEX

`.` means “any single character” except newline
`*` zero or more of the preceding match
`+` one or more of the preceding match
`[abc]` any one character of a, b, and c
`(RX1|RX2)` either something that matches RX1 or RX2
`^` the start of the line
`$` the end of the line

