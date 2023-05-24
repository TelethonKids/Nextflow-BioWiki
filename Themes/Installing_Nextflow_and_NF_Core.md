## Basecamp

### `PATH` and user-local `bin` folder

```console

mkdir $HOME/bin

export $PATH="$PATH:$HOME/bin"

```
### `micro` Text editor:

A program used to edit plain text files, create and edit files based in various programming languages, handle “hand-coding” of many different languages.

What is micro? Terminal based [text editor](https://micro-editor.github.io/), no dependencies, easy to use and intuitive Smart and intuitive terminal orientated text editor, used for editing SSH files and other terminal tasks 

- https://github.com/zyedidia/micro
- https://micro-editor.github.io/

```console
curl https://getmic.ro | bash
```

- Built in help pages (Ctrl-E + help topic OR Ctrl-G), also help pages built into GitHub repository (https://github.com/zyedidia/micro)
- Able to be used in a modern terminal (MacOS, Windows, Linux, etc.)
- Similar keybindings/shortcuts compared to Microsoft word (save, copy, paste, undo)
- Similar to the text editor nano
- Install using prebuilt binary, quick-install script, eget, package managers (brew - Mac, snap – Linux, as well as many other package managers

To make the addition of `$HOME/bin` change permanent, let's update the `~/.bashrc` 

```console 
micro ~/.bashrc
```

```
export $PATH="$PATH:$HOME/bin"
```


References:
    - (Purpose of bin directory)[https://unix.stackexchange.com/questions/237152/purpose-of-bin-directory#:~:text=Bin%20is%20an%20abbreviation%20of,aren't%20used%20to%20them]

