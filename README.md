# Rushi

### _Note: none of this is implemented :)_

Rushi is an esoteric shell that aims to replace reasonable scripting langauges with rust, a 
syntax heavy language for systems and not 1 liners.

In a normal shell you would issue a command that looks like this:
```sh
selection = $(ls -a1 code | grep .rs | fzf -i -m)
cat $selection | tail

# or

cat $(ls -a1 code | grep .rs | fzf -i -m) | tail
```

In rushi it would look like this:
```rushi
let selection = code.ls(-a1).fzf(-i -m)
cat(selection).tail

// or 

cat(code.ls(-a1).fzf(-i -m)).tail
```

So much better right?

## Parsing

The code uses a trimmed version of rustc to compile your code to an AST (abstract syntax tree).
The AST is then passed to an interpreter which runs it. When you call a meathod the interpreter
checks for this (in order):
    1. is it a builtin meathod
    2. is it a part of coreutils package (optional dependency)
    3. is it there an .rlib in your rpath with that name
    4. is it in your PATH 
    5. interpreting as string (in some contexts)
    6. error


## Goals

The main goal of rushi is to be dumb and have a bit of a giggle. However secondary, there is a 
goal that by knowing rust you can do everything on a computer and this is the next step in that.
I don't want this to be something that just marginally changes things like nuShell or fish and 
ends up feeling luke warm. This project is dumb is proud of it.

## Notes

I talked with a few people and asked them something along the lines of "if using a terminal was 
easy and you knew it was faster would you use it?" and all of them responded with no. This means 
that people are just dumb and as such there no reason to appeal to normies and make stuff "nice"
or "friendly". As such this shell is designed to be evil. 