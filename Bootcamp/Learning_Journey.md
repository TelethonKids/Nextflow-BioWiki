
# Learning Journey

<br>

![Overview](/Bootcamp/_images/Bootcamp_schedule.png)


### December 4<sup>th</sup>

- Local infrastructure and resources:
    * Guide to online and accessble virtual environments and coding spaces
    * Exploration and installation of Gitpod/Codespace
    * Verification and configuration of personal Telethon Kids Institute VMs
    * Provide Biowiki resources and relevant guides and information

### December 5<sup>th</sup>

- Introduction to nf-core:
    * What is nf-core?
    * How does nf-core work?
    * What are community best practices?
    * Where can you go to find this information?
    * Where can you go to get one-on-one help?
    * Overview of available tools
- Toy pipeline development: <br>
*To show the basic structures of pipelines (not nf-core style)*
    * Making a small pipeline
        * Make first process and a workflow block
        * Make a second process and join with the operators
            - Include metadata
        * Add a container for software
        * Use directives to allocate resources
- nf-core repository, configurations, and deploying pipelines
    * Structures of nf-core repositories
    * Building run commands using demo pipelines
    * Where are configs found and what are their orders of priority:
        * Deploying pipeline with custom parameters
        * Deploying pipeline with custom params files
        * Deploying pipeline wth config file and selectors
        * What could be conflicting results?

### December 6<sup>th</sup>
- nf-core repository, configurations, and deploying pipelines *Continuation*
- `nf-core/fetchngs` and `nf-core/rnaseq`:
    * Focusing on usage of these specific pipelines
    * Running the pipelines with various parameter choices
    * Configurations and pipeline parameters specific to your data
    * Recognition of resources and troubleshooting

    ### December 7<sup>th</sup>
- `nf-core/mag` and `nf-core/ampliseq`:
    * Focusing on usage of these specific pipelines, with a microbiome focus
    * Running the pipelines with various parameter choices
    * Configurations and pipeline parameters specific to your data
    * Recognition of resources and troubleshooting
- Building nf-core pipeline and customisation
    * Creating an nf-core pipeline with custom input data
    * Adding modules and subworkflows to the custom pipeline
    * Adding logics to include and exclude subworkflows being executed
    * Adding local modules and patching
    * Add a custom script in bin