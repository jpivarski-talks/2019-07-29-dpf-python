# 2019-07-29-dpf-python

Tutorials for the [IRIS-HEP tutorial at APS DPF](https://indico.cern.ch/event/782953/sessions/302485/#20190729), July 29, 2019, 2‒6pm in Shillman 425, Northeastern University.

## How to participate

The preferred way to participate is to run the JupyterLab code with us, altering examples and asking us "what if" questions as we go along, as well as using the notebooks as starting points for the five-minute exercises.

You can run all of these notebooks on a public cloud service called Binder:

<p align="center">
  <a href="https://mybinder.org/v2/gh/jpivarski/2019-07-29-dpf-python/1.0?urlpath=lab">
    <img src="https://mybinder.org/badge_logo.svg" alt="Launch Binder" height="40">
  </a>
</p>

Navigate in the JupyterLab file view (left sidebar) to the desired lesson. Note that Binder cannot save data permanently (reloading your web browser will take you to a new instance), and it may take a minute or two to start up.

## Running everything on your own computer

Alternatively, you might want to follow along using your own computer so that you can save data and have copies of the software after the tutorial. If you want a copy of all software packages (a few GB) and you have a non-Windows computer, install [conda](https://docs.conda.io/en/latest/miniconda.html) and [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and clone this repository:

```bash
git clone https://github.com/jpivarski/2019-07-29-dpf-python.git
cd 2019-07-29-dpf-python
```

Then use

```bash
conda env create -f environment.yml
```

to install nearly everything in an isolated environment named `dpf-python`. You can delete this without affecting anything else with the command `conda remove --name dpf-python --all`.

To _use_ the software, you have to enter the isolated environment. Type

```bash
conda activate dpf-python
```

to enter the environment (and exit it by closing the terminal or `conda deactivate`). One additional package, JupyterLab, must be installed manually in the isolated environment:

```bash
conda install jupyterlab
```

Start JupyterLab by typing

```bash
jupyter lab
```

A web browser tab should open with the same environment as the Binder site above, or a URL will be provided that you can copy-paste into a web browser. However, the software will be running on your computer.

## Cherry-picking software packages or manually installing

Chances are, you won't want to install _everything_ defined by `environment.yml`, only the packages most relevant to your work. They can be installed individually with pip or conda. There are, however, a few constraints:

   * ROOT can be installed with conda on Macs and UNIX-like computers (e.g. Linux), but not with conda on Windows and not with pip. You can install ROOT manually, but be sure to install the latest version, [release 6.18/00](https://root.cern/content/release-61800) to get the `RDataFrame.AsNumpy` feature. Also, interaction between ROOT and Python might not work if the compile-time and runtime versions of Python differ. Note that conda installs a custom Python version and pip doesn't.
   * We do very little with `root-numpy`, but if you install this package, it should be with pip and it should be after ROOT and Python are already installed because it compiles against both of them.
   * The tutorial examples use Python [f-strings](https://realpython.com/python-f-strings/) for formatting; these require at least Python 3.6. None of the exercises have been tested with Python 2, though most of the software described in this tutorial will support Python 2.7 until it reaches its end of life in December 2019.
