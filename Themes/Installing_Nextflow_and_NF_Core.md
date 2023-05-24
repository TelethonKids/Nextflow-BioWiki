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
    - [StackExchange - Purpose of bin directory](https://unix.stackexchange.com/questions/237152/purpose-of-bin-directory#:~:text=Bin%20is%20an%20abbreviation%20of,aren't%20used%20to%20them)

## Checkpoint-1

### `sdkman`

"Software Development Kit Manager" https://sdkman.io/ 
Tool for managing parallel version of multiple Software Development Kits
Java new release cycle, developers need to manage parallel versions and different builds of SDKs in their environment, SDKman helps with managing installation and selection of the SDKs (as opposed to constantly setting path variables) https://www.baeldung.com/java-sdkman-intro
sdkman: tool to manage parallel versions of multiple SDKs, convenient in command line for listing, installing, switching, and removing SDKs, also sets environmental variables, also supports downloading of other Java-like/based languages (https://www.baeldung.com/java-sdkman-intro)
Java, programming language, runtime – apps written in Java interpreted by Java Virtual Machine (JVM), allows it to run on all other platforms despite writing on another
Programming language and application may develop at different rates – Java advances version while application running with may not be; for two applications need to use that require different Java versions may need to install both on same system – SDKman allows for management of your different Java versions and related languages
ESSENTIALLY – package manager for Java https://opensource.com/article/22/3/manage-java-versions-sdkman
## add installation code, and any other help usage code at the end (https://github.com/sdkman/sdkman-cli)

