## Basecamp

![Overview](_images/vm_setup.png)

### `PATH` and user-local `bin` folder

```console

mkdir $HOME/bin

export PATH="$PATH:$HOME/bin"

```


### `zip` and `unzip`

Make sure that your VM has the `zip` and `unzip` tools installed, in some cases this might need assitance from your administrator

```console
sudo apt install zip unzip

```
### `micro`

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
export PATH="$PATH:$HOME/bin"
```


References:
    - [StackExchange - Purpose of bin directory](https://unix.stackexchange.com/questions/237152/purpose-of-bin-directory#:~:text=Bin%20is%20an%20abbreviation%20of,aren't%20used%20to%20them)

## Checkpoint-1

### `sdkman`

https://sdkman.io/

"Software Development Kit Manager"  - a tool for managing parallel version of multiple Software Development Kits. 

We will use this essentially as a package manager for Java 

```console
curl -s "https://get.sdkman.io" | bash 
exec $SHELL
```

References
    - https://opensource.com/article/22/3/manage-java-versions-sdkman

### `java`

Programming language and computing platform, platform on which many services and applications are built 

```console 
sdk install java 17.0.6-amzn
```
References:
    - https://www.java.com/en/download/help/whatis_java.html

### `nextflow`

A workflow engine and language that enables scalable and reproducible scientific pipelines 

Allows for parallelisation and distribution computing – nextflow based on dataflow programming model, simplifies parallelisation

```
cd $HOME/bin

wget -qO- https://get.nextflow.io | bash

```
References:
    - https://github.com/nextflow-io/nextflow
    - [Story of Nextflow](https://elifesciences.org/labs/d193babe/the-story-of-nextflow-building-a-modern-pipeline-orchestrator)

## Checkpoint-2

### `conda` and `micromamba`

An open source _package management system_, and environment management system, able to install, run, and update packages and any dependencies, save and switch between environments, can package and distribute software from any language () 

Conda is an environment manager, switch between multiple environments with different dependencies, languages and softwares

Conda environments similar to virtual environments (pythons virtualenv), more powerful since mamba able to manage native dependencies and downloaded ones, able to generalise the virtual environment to many programmed languages


```console
wget https://repo.anaconda.com/miniconda/Miniconda3-py310_23.3.1-0-Linux-x86_64.sh

bash Miniconda3-py310_23.3.1-0-Linux-x86_64.sh -b -p $HOME/miniconda

$HOME/miniconda/bin/conda init

exec $SHELL
```

After the above steps, your shell prompt should now mention the `(base)` environment as shown below

```
(base) ubuntu@lung-virome:~$

```

`micromamba` is a minimal single-binary command line tool that is used to manage conda environments. 
The core benefit of `micromamba` is the installation speed of softwares, we shall need it when we run bigger pipelines (e.g. `nf-core/rnaseq`)

```console
curl micro.mamba.pm/install.sh | bash
```

Cheatsheets: 
    - https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf 
    - https://docs.conda.io/projects/conda/en/latest/_downloads/843d9e0198f2a193a3484886fa28163c/conda-cheatsheet.pdf

References
    - https://docs.conda.io/en/latest/

### `rnaseq-nf` for sanity check

The `nextflow-io/rnaseq-nf` is a "toy" Nextflow pipeline which is often used for making sure that the infrastructure is setup correctly.

We'll rely on this pipeline and test our `conda` setup.

```console
nextflow run nextflow-io/rnaseq-nf -profile conda

```
## Checkpoint-3

### `tmux` (or `screen`)

Once we have all the building blocks setup, we can start running the pipelines in background using tools like `tmux` or `screen`

Terminal multiplexer, allows for increased productivity and session management

Allows you to switch between several programs/pages/windows/sessions in one
terminal, detach them (while they keep running in the background), and reattach
them (in different terminals) (https://github.com/tmux/tmux/wiki)


Resources:

- Github: https://github.com/tmux/tmux/wiki
- Manual page server: https://manpages.ubuntu.com/manpages/xenial/en/man1/tmux.1.html
- Getting started page: https://github.com/tmux/tmux/wiki/Getting-Started

Cheatsheets: 
- https://quickref.me/tmux.html
- https://github.com/tmux/tmux/wiki/Getting-Started
- https://tmuxcheatsheet.com/ 
- https://gist.github.com/henrik/1967800

## Checkpoint-4

### `nf-core` tool

The `nf-core` community has created a best-practices tool called `nf-core` which could be used to download and run existing pipelines as well as to create new pipelines from scratch.

```console
pip install -U nf-core
```

We shall make use of this tool to download the `nf-core/rnaseq` (the _full_ rnaseq pipeline)


```console
nf-core download rnaseq
```

After the following command just follow the prompts to 
- Select which version of the pipeline to download
- Download all the singularity containers

### Custom config file 

Sometimes, to fully customize the pipeline as per the VM or some pre-installed conda-environments it might be necessary to create a custom `.config` file.

If you have some pre-existing conda environments you could instruct the pipeline to use that environment instead of creating new using the process selectors 

```nextflow

//NOTE: Use pre-existing environment
process {
    withName: "SALMON_INDEX" {
        conda "bioconda::salmon=1.10.1"
    }
}


```

Or you could limit the number of parallel executions by appending this snippet in the config file

```nextflow

executor {
    queueSize = 4
}

```

To use this custom file, append `-c custom.config` to the `nextflow run ...` command, for example

```console
nextflow run nf-core/rnaseq \
    -profile test,conda \
    -c custom.config \
    --outdir <OUTDIR>
```

## Summit

Congratulations for making it to the Summit! 

You have done admirably well in setting up your VM for running any Nextflow pipeline.
