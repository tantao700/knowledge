# VIM

## [{number}] + {command} + {text object or motion}
- diw - delete in word
- caw - change all words

- dd/yy - delete/copy a line
- D/C - delete/change until end of line

- I/A - move to the beginning/end of line
- o/O - insert new line above/below current line and insert
- ^/$ - until start/end of line


## Text Objects
- w - words
- s - sentences
- p - paragraphs
- t - tags  # tags available in XML/HTML files

## Motions
- a - all
- i - in
- t - 'til
- f - find forward
- F - find backward

## Commands

- d -delete(also cut)
- c -change(delete,then place in insert mode)
- y -yank (copy)
- v -visually select

## Cmd Set
- r!req 10 # gen a 1-10 set
- 1,+1d    #range form 1 to current cursor +1  ,then to delete
- 1;+1d    #range 1,2 to delete
- ci{char} ci" ci' ci}       # change insert "符号内的字符
- di{char} di" di' di}       # delete insert "符号内的字符
- vi{char} vi" vi' vi}       # selete insert "符号内的字符
- yi{char} yi" yi' yi}       # yank(copy) insert "符号内的字符




## Macro
A sequence of commands recorded to a register

### Macro:record a marco
- q{register}
- (do the things)
- q

### Macro:play a macro
- @{register}


## Plugins
- Plug - Plugin manager
- nerdtree - file drawer
- ctrlp - fuzzy file finder
- fugitive - git tool
- syntasitic - syntax checker/linter
