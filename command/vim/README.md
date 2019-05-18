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