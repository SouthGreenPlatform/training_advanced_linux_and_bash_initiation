[![CC BY NC SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]


# Advanced linux and bash initiation training
---------------------------

<img src="SouthGreen.png" /> 

## Table of Contents

   * [Foreword](#foreword)
   * [Project layout](#project-layout)
   * [For collaborators teachers and developers](#for-collaborators-teachers-and-developers)     
     * [Modify content](#modify-content)   
     * [MkDocs](#mkdocs)
        * [Welcome to MkDocs](#welcome-to-mkdocs)
        * [Installation](#installation)
          * [Manual](#manual)
          * [Conda](#conda)
        * [Testing and building the website](#testing-and-building-the-website)
   * [Acknowledgement](#acknowledgement)
   * [License](#license)


## Foreword

The course itself lives [https://southgreenplatform.github.io/training_advanced_linux_and_bash_initiation](https://southgreenplatform.github.io/training_advanced_linux_and_bash_initiation/),
where you can find all the relevant information.  


## Project layout

```
    README.md               # General readme 
    mkdocs.yml              # The configuration file for the site rendering.
    conda_env.yml           # Conda env to build and test the site locally
    docs/                   # material that will be publish with the static web site
        index.md            # The documentation homepage (Website Home page).
        pages/              # Folder dedicated to the course materials use by mkdocs for the website
            images          # Images used in the course materials in general
            xxx/            # Folder containning the course materials for one topic
                xxx.md      # Page taking about all or a part of the topic
                images/     # Images related to the topic
            ...    
        lectures/           # Folder dedicated to lectures (within docs to ease embedding within the course)
            README.md       # readme
            environment.yml # conda env to use for rendering the Rmarkdown lecture files
            template.css    # CSS used by all Rmarkdown lecture files
            Snakefile       # Automating rendering of all Rmarkdown lecture files
            xxx             # folder related to one lecture
                xxx.Rmd     # Lecture in Rmarkdown format
                xxx.pdf     # PDF rendering of Rmarkdown file
                xxx.html    # HTML rendering of Rmarkdown file
    tutorials/              # Folder dedicated to tutorials
        xxx                 # folder related to one tutorial
    Images                  # Images used in the README
```  

## For collaborators teachers and developers

This part is for collaborators-teachers and developers.

### Modify content

When you are in the repository, add and/or modify your markdown tutorials in the docs directory.
The arborescence of the website menu is to setup in the `mkdocs.yml` file

### Mkdocs

#### Welcome to MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).  
For full documentation about the [material mkdocs theme](https://squidfunk.github.io/mkdocs-material/).

#### Installation

##### Manual

As prerequisite you need python >=3.8 and pip.  

Install Mkdocs:

`pip install mkdocs`

For the theme:  
`pip install mkdocs-material`

For the extensions:  
`pip install pymdown-extensions`

For the plugins:  
`pip install mkdocs-minify-plugin`  
`pip install mkdocs-macros-plugin`

##### Conda

Clone the repository and move in it.  
Then install all dependencies using conda and the `conda_env.yml` shipped with this repo:

```
conda env create -f conda_env.yml
```

Activate the environment and you are good:

```
conda activate education
```

#### Testing and building the website


* `mkdocs serve` - Start the live-reloading docs server, to test the site locally (http://127.0.0.1:8000/).
* `mkdocs gh-deploy` - Deploys the site on github pages.

* `mkdocs build` - Build the documentation site.
* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs -h` - Print help message and exit.



##  Acknowledgement

 * Anne-Muriel Chiffoleau (UM)
 * Jacques Dainat for the conversion of this material for use in mkdocs
 * All contributors

## License

This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY%20NC%20SA%204.0-lightgrey.svg
