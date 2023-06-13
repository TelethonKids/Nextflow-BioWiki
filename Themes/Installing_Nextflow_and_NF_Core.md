## Basecamp

![Overview](_images/vm_setup.png)

### `PATH` and user-local `bin` folder

The `bin` directory is where the user of the operating system can find their appplications, and all executable binary executables. Contains shells like bash and other commonly used commands.

```console

mkdir $HOME/bin

export PATH="$PATH:$HOME/bin"

```

**References:**
- [Stack Exchange - Purpose of bin directory](https://unix.stackexchange.com/questions/237152/purpose-of-bin-directory#:~:text=Bin%20is%20an%20abbreviation%20of,aren't%20used%20to%20them)


### `zip` and `unzip`

Make sure that your VM has the `zip` and `unzip` tools installed, in some cases this might need assitance from your administrator

```console
sudo apt install zip unzip

```
### `micro`

A text editing program is used to:
- edit plain text files 
- create files, and 
- edit files based in various programming languages

Text editors are able to handle “hand-coding” of many different languages.

What is [`micro`](https://github.com/zyedidia/micro)? A Terminal based [text editor](https://micro-editor.github.io/) with no dependencies, is easy to use, and is smart and intuitive, mainly being used for editing SSH files and other terminal tasks.

`micro` contains built in help pages through terminal (Ctrl-E + help with the option of adding a topic, OR Ctrl-G), and alsohas  help pages in a GitHub repository (https://github.com/zyedidia/micro).

`micro` is able to be used in a modern terminal (MacOS, Windows, Linux, etc.), and contains similar keybindings/shortcuts to Microsoft Word (save, copy, paste, undo), and is similar to the text editor nano.

Installation through:
- prebuilt binary 
- quick-install script 
- eget, and
- package managers (brew - Mac, snap – Linux)

>  Quick-install script:
>
>```console
>curl https://getmic.ro | bash
>```
>

To make the addition of `$HOME/bin` change permanent, let's update the `~/.bashrc` 

```console 
micro ~/.bashrc
```

```
export PATH="$PATH:$HOME/bin"
```


**References:**
- [Tech basics: An introduction to text editors](https://online.york.ac.uk/tech-basics-an-introduction-to-text-editors/)
- [Micro](https://github.com/zyedidia/micro)
- [Micro editor](https://micro-editor.github.io/)


## Checkpoint-1

### `sdkman`

"Software Development Kit Manager"  - a tool for managing parallel version of multiple Software Development Kits. 

`sdkman` assists as a Java package manager which manages parallel versions of SDKs and their environments, while assisting with installation management and SDK selection.

For developers to manage parallel versions of SDKs, in command line `sdkman` helps with:
- listing,
- installing
- switching
- removing, and
- setting environment variables

Programming languages and their applications can develop at varying rates, so `sdkman` manages these Java versions and other related languages.

We will use this essentially as a package manager for Java 

```console
curl -s "https://get.sdkman.io" | bash 
exec $SHELL
```

**References:**
- [SdkMan: The Software Development Kit Manager](https://sdkman.io/)
- [Guide to SDKMAN](https://www.baeldung.com/java-sdkman-intro)
- [Manage Java versions with SDKman](https://opensource.com/article/22/3/manage-java-versions-sdkman)

### `java`

"Write once and run anywhere." - `java` has the ability to run on any device, with any hardware system, and other hardware components.

`java` is a programming language and computing platform on which many services and applications are built. 

`java` is an object-orientated programming language and software platform, that is able to run on many devices.

```console 
sdk install java 17.0.6-amzn
```
**References:**
- [How Java works](https://www.ibm.com/topics/java)
- [What is Java technology and why do I need it?](https://www.java.com/en/download/help/whatis_java.html)

### `nextflow`

`nextflow` is a workflow engine and language that is portable and able to function on a variety of platforms. The purpose of `nextflow` is to enable portable workflows that allow for scalable and reproducible scientific pipelines.

`nextflow` allows for parallelisation and distribution computing, and is based on a dataflow programming model. `nextflow` simplifies parallelisation through composing many different processes, which allows for coordination and synchronisation through specifying inputs and outputs.

```
cd $HOME/bin

wget -qO- https://get.nextflow.io | bash

```
**References:**
- [Nextflow Github](https://github.com/nextflow-io/nextflow)
- [Story of Nextflow](https://elifesciences.org/labs/d193babe/the-story-of-nextflow-building-a-modern-pipeline-orchestrator)
- [Nextflow](https://www.nextflow.io/)

## Checkpoint-2

### `conda` and `micromamba`

Containers are a form of operating system visualisation that allow for building, testing, and redeoplying applications in multiple environments on a single machine. Containers are there to build, share, and run applications through packaging code and all of its dependencies.

`conda` is an open source _package management system_ and _environment management system_ that is able to install, run, and update packages and any dependencies, as well as save and switch between different environments. `conda` is able to package and distribute software from any language.

`conda` as an environment manager is able to switch between multiple environments that each have different dependencies, languages and softwares.


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

Mamba environments are similar to virtual environments (pythons virtualenv), however they are more powerful since mamba is able to manage native dependencies and downloaded ones. Mamba is a cross-platform manager that is compatible with conda packages, and is able to generalise virtual environments to many programmed languages. Mamba is known for its higher speed and more relaible environment solutions.

`micromamba` is a small version of the mamba package manager. `micromamba` is a minimal single-binary command line tool that is used to manage conda environments. 

The core benefit of `micromamba` is the installation speed of softwares, we shall need it when we run bigger pipelines (e.g. `nf-core/rnaseq`)

```console
curl micro.mamba.pm/install.sh | bash
```

Cheatsheets: 
- [Conda Cheat Sheet](https://docs.conda.io/projects/conda/en/latest/_downloads/843d9e0198f2a193a3484886fa28163c/conda-cheatsheet.pdf) 
- [Mamba Quick Start Guide](https://mamba.readthedocs.io/en/latest/user_guide/micromamba.html)

**References:**
- [What are containers?](https://www.netapp.com/devops-solutions/what-are-containers/)
- [Use containers to build, share, and run your applications](https://www.docker.com/resources/what-container/)
- [Conda](https://docs.conda.io/en/latest/)
- [Mamba Documentation](https://mamba.readthedocs.io/en/latest/)


### `rnaseq-nf` for sanity check

The `nextflow-io/rnaseq-nf` is a "toy" `nextflow` pipeline which is often used for making sure that the infrastructure is setup correctly. `rnaseq-nf` is a basic pipeline that is used for quantification of genomic features from short read data, and is implemented with `nextflow`.

We'll rely on this pipeline and test our `conda` setup.

```console
nextflow run nextflow-io/rnaseq-nf -profile conda

```
References
- [RNAseq-NF pipeline Github](https://github.com/nextflow-io/rnaseq-nf)

## Checkpoint-3

### `tmux` (or `screen`)

Once we have all the building blocks setup, we can start running the pipelines in background using tools like `tmux` or `screen`

`tmux` is a terminal multiplexer that allows for increased productivity and session management, while also protecting your running processes from connection dropouts.

In one terminal, `tmux` allows you to switch between several:
- programs
- pages
- windows, and
- sessions 

 All the while allowing you to detach them, while they keep running in the background, and reattach them in different terminals. `tmux` allows for multiple sessions with multiple windows that are each running different processes, while being set in different environments, to run in the background simultaneously.


Resources:
- [Tmux Github](https://github.com/tmux/tmux/wiki)

Cheatsheets: 
- [Quick ref: tmux cheat sheet](https://quickref.me/tmux.html)
- [Github: tmux getting started](https://github.com/tmux/tmux/wiki/Getting-Started)
- [Tmux cheat sheet & quick reference](https://tmuxcheatsheet.com/) 
- [Tmux cheat sheet](https://gist.github.com/henrik/1967800)
- [Ubuntu manuals: tmux](https://manpages.ubuntu.com/manpages/xenial/en/man1/tmux.1.html)

> Quick tip:
> `tmux` cheat sheets are readily available online. Searching a query will more than likely lead to a relevant cheat sheets or user guides.

**References:**
- [Tmux getting started](https://github.com/tmux/tmux/wiki/Getting-Started)
- [Tmux manual page](https://man.openbsd.org/OpenBSD-current/man1/tmux.1)
- [Tmux github](https://github.com/tmux/tmux/wiki)


## Checkpoint-4

### `nf-core` tool

The `nf-core` community is where a range of tools and pipelines are shared to help other users get a handle on `nextflow` and its implementation. A large amount of help and documentation is available for those learning `nextflow` and its pipelines.

> Within `nf-core` tools you are able to access help pages, pipeline repositories, and other resources. To see all available pipelines use the `-help` tag for manuals and guides:
> - [Getting started with nf-core](https://nf-co.re/usage/tutorials/nf_core_usage_tutorial)
> - [Tools](https://nf-co.re/tools/#installation)

The `nf-core` community has created a best-practices tool called `nf-core` which could be used to download and run existing pipelines as well as to create new pipelines from scratch.

```console
pip install -U nf-core
```

We shall make use of this tool to download the `nf-core/rnaseq` (the _full_ rnaseq pipeline).


```console
nf-core download rnaseq
```

After the following command, just follow the prompts to 
- Select which version of the pipeline to download
- Download all the singularity containers

**References:**
- [Getting started with nf-core](https://nf-co.re/usage/tutorials/nf_core_usage_tutorial)

### Custom config file 

To run `nf-core` pipelines, `nexflow` must be installed, as well as a packaging tool (`conda`, Docker, Singularity). With `nextflow` having the built-in functionality to fetch pipelines, All that is needed to run a pipeline locally is:
- install packaging tool
- install `nextflow`
- installl `nf-core` (tools)
- `nextflow` FETCH pipeline
- run

> For tutorials and other help guides go to [Getting started with nf-core](https://nf-co.re/docs/usage/tutorials/nf_core_usage_tutorial#running-nf-core-pipelines).

Sometimes, to fully customize the pipeline as per the VM or some pre-installed `conda`-environments it might be necessary to create a custom `.config` file.

If you have some pre-existing `conda` environments, you could instruct the pipeline to use that environment instead of creating a new one using the process selectors.

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

You have done admirably well in setting up your VM for running a Nextflow pipeline.
