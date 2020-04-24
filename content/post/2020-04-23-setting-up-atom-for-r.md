---
title: Setting up Atom to use with R (and Python)
author: ''
date: '2020-04-23'
slug: setting-up-atom-for-r
categories:
  - R
  - Python
tags: ["atom"]
image:
  caption: ''
  focal_point: ''

---
I recently got myself a new laptop (HP Pavilion x360) to make it easier for myself to work from home during this pandemic. Since both my home and work desktop computers have Ubuntu 18.04 set up, it was quite a change to work with Windows again. I actually want to keep Windows on this one because I still haven't found a good alternative for Microsoft Office (if you do have one, please let me know.) I honestly love this new laptop but it was quite frustrating to keep having to remember the Shell differences between Windows and Linux, among other things. At the same time, I was looking for a cross-language IDE to use with R and Python but that could be extended to other languages. I currently use RStudio but have never been entirely satisfied with it. That how I ended up with **Atom**.

**Basically, what I was looking for was:**
* To be able to work with and switch scripts using different languages within the same IDE but in self-contained environments.
* To have all my plots and output within the IDE as in RStudio. I hate having pop-up windows when working on a smaller screen.
* To be able to execute code line by line as in RStudio.
* To have easy access to a bash terminal.
* Git integration
* All the other usual stuff: autocompletion, syntax colouring, auto-indentation...

I've only used Atom for about two days now and I'm already in love with my new tool and will definitely be sticking with it for a while. I still wanted to be able to use RStudio since I still haven't found a plugin for Rmarkdown files and it's easier when doing demonstrations for students since this is what they use. So below is a guide to set up R and Python, using the current RStudio set up.

## Setting up Python using Anaconda
While it makes it easier to set up both languages through Anaconda instead of using the individual R/Python Managers, I couldn't figure out how to use R in RStudio under an Anaconda set up. Nor was my final Atom set up working with my R setup.

### Installing Anaconda
You have the option of installing the full Anaconda distribution but it's quite big and you may never use all the features it offers. Instead, go for Miniconda instead. You can find the GUI installers [here](https://conda.io/miniconda.html).

After installing it, you'll need to add it to your system `PATH`.   Hit the `windows` key → enter `environment` → choose from `settings` → `edit environment variables for your account` → `Environment Variables` → select `Path variable` → `Edit` → `New`. You'll want to add both the
`miniconda3` folder and the `Scripts` folder within that.


```
# Paths to add to system variables
"C:\Users\<username>\miniconda3\"
"C:\Users\<username>\miniconda3\Scripts"
```

### Setting up Python and the Python kernel
Once the above is completed, you can use `conda` to install python and python packages. You'll want to create a new environment first or you can just use the `base` environment. To start using `conda`, open command prompt:

```
# creating a conda environment. Only use conda create to use base
conda create --name myconda python=3

# to work within the new conda environment
activate myconda
```

Then use the following to install the necessary packages to setup python and the python kernel.

```
conda install ipython ipykernel python-language-server
```

### Setting R and the R kernel
I'm assuming that R is already set up on your machine. Open R and install the package `languageserver` and `IRkernel`

```
install.packages(c("languageserver", "IRkernel"))
```
This can also be done via the terminal if you have R in your system `PATH`:

```
Rscript -e "install.packages(c('languageserver', 'IRkernel'), repos = 'https://cloud.r-project.org')"
```

## Download and configure Atom

You can install [Atom](https://atom.io/) from the official website in whatever manner works for you. Our setup will be based around a couple of Atom packages:

* [PlatformIO IDE Terminal](https://atom.io/packages/platformio-ide-terminal) - an integrated terminal for Atom
* [Atom IDE](https://atom.io/packages/atom-ide-ui) and its [Python](https://atom.io/packages/ide-python) and [R](https://atom.io/packages/ide-r) extensions.
* [Hydrogen](https://atom.io/packages/hydrogen) - a Jupyter-like extension which allows to execute code interactively with results appearing inline, just like R notebooks.
* [Hydrogen Launcher] - connecting the Hydrogen to the PlatformIO terminal to share the same interactive session.

Once, you've install Atom, you can use the GUI to install the above packages or you can use the terminal again for that:

```
# install hydrogen and terminal
apm install hydrogen hydrogen-launcher platformio-ide-terminal

# install language/IDE plugins
apm install atom-ide-ui ide-python ide-r language-r
```

The `language-r` extension requires some patching to avoid an error message on start up. Open the `~/.atom/packages/language-r/snippets/language-r.cson` file and look for `Cumulative max` and `Grep`. Both of these have duplicate entries, so change the duplicates to `Cumulative max 2` and `Grep 2` respectively.

Once this is done, it's finally time to install our R and Python kernels so that Hydrogen knows about them.

```
python -m ipykernel install --user
Rscript -e 'IRkernel::installspec()'
```

And you're (and I am as well) now ready to use Atom with both R and Python!
