# Day 6 - Editing with "vim"

https://github.com/snori74/linuxupskillchallenge/blob/master/06.md  
https://www.youtube.com/watch?v=dNd3BvJNDIo  

## basic usage
commands
```
:q => quit
:q! => quit without saving
:w => save changes
:wq => save changes and close
:w /path/to/filename => save as
```
## navigation
arrow keys or 
- h => ←
- j => ↓
- k => ↓
- l => →
- gg => go to file beginning
- G => go to file end

## change modes
- i => switch to insert mode
- esc => switch to normal mode
- v => switch to visual mode
- : => switch to command mode

## editing
- x => delete one character after cursor
- dd => delete entire line

### select text
1. v => switch to visual mode
2. use arrow keys to select text 

### delete, cut, copy, undo...
- d => to delete selected text
- y => to copY selected text
- yy => to copY entire line
- p => to paste copied text
- u => Undo
- Ctrl + R ? => Redo

## find
- / => find
- n => Next search result
- N => previous search result

## find and replace
1. : => switch to command mode
2. %s/<regex>/<replacement text>/c => confirm and replace found text 

## extra
[Christopher Okhravi - My Vim Setup #1](https://www.youtube.com/watch?v=Scp0rhN3usU)  
[Christopher Okhravi - My Vim Setup #2](https://www.youtube.com/watch?v=SEa9YOXk6MQ)  

