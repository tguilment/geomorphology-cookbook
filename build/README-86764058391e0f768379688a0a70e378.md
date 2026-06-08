# Geomorphology Cookbook

<img src="thumbnails/thumbnail.png" alt="thumbnail" width="300"/>

[![nightly-build](https://github.com/ProjectPythia/cookbook-template/actions/workflows/nightly-build.yaml/badge.svg)](https://github.com/ProjectPythia/cookbook-template/actions/workflows/nightly-build.yaml)
[![Binder](https://binder.projectpythia.org/badge_logo.svg)](https://binder.projectpythia.org/v2/gh/ProjectPythia/cookbook-template/main?labpath=notebooks)
[![DOI](https://zenodo.org/badge/475509405.svg)](https://zenodo.org/badge/latestdoi/475509405)

_See the [Cookbook Contributor's Guide](https://projectpythia.org/cookbook-guide) for step-by-step instructions on how to create your new Cookbook and get it hosted on the [Pythia Cookbook Gallery](https://cookbooks.projectpythia.org)!_

This Project Pythia Cookbook covers ... (replace `...` with the main subject of your cookbook ... e.g., _working with radar data in Python_)

## Motivation

- What: A cookbook adapting ArcGIS PRO workflow in Geoscience Australia’s Semi-automated Morphological Mapping Tools (GA-SaMMT) for open science.
- Why: Seafloor morphology maps supports marine geoscience, habitat mapping, and environmental management. However, many workflows remain manual or difficult to reproduce (e.g. ArcGIS Pro tools)
- How: Starting from GeoTIFF bathymetry, the cookbook will compute terrain metrics, delineate candidate features, and produce GIS-compatible labeled polygons for landforms (e.g. valleys, ridges, depressions, and plateaus.) with notebook visualization
- Who: This project is for anyone interested in geomorphology, bathymetry, GIS, and Python geospatial in general.

## Authors

First Author, Second Author, etc. _Acknowledge primary content authors here! You can include links to their GitHub profiles or other unique pages._

### Contributors

<a href="https://github.com/ProjectPythia/cookbook-template/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=ProjectPythia/cookbook-template" />
</a>

## Structure

(State one or more sections that will comprise the notebook. E.g., _This cookbook is broken up into two main sections - "Foundations" and "Example Workflows."_ Then, describe each section below.)

### Section 1 ( Replace with the title of this section, e.g. "Foundations" )

(Add content for this section, e.g., "The foundational content includes ... ")

### Section 2 ( Replace with the title of this section, e.g. "Example workflows" )

(Add content for this section, e.g., "Example workflows include ... ")

## Running the Notebooks

You can either run the notebooks in the Cookbook using [Binder](https://binder.projectpythia.org/) or on your local machine.

### Running on Binder

The simplest way to interact with a Jupyter Notebook is through
[Binder](https://binder.projectpythia.org/), which enables "one click"
execution in the cloud. Simply navigate your mouse to
the top right corner of the book chapter you are viewing and click
on the rocket ship icon (see screenshots [here](https://foundations.projectpythia.org/preamble/how-to-use/#running-pythia-foundations-examples)),
and a text box will appear. Type or paste the Pythia Binder link
(`https://binder.projectpythia.org`) and click "Launch".
After a few moments you should be presented with a
notebook that you can interact with. You’ll be able to execute code
and even change the example programs. At first the code cells
have no output, until you execute them by pressing
{kbd}`Shift`\+{kbd}`Enter`. Complete details on how to interact with
a live Jupyter notebook are described in the Pythia Foundations chapter [Getting Started with
Jupyter](https://foundations.projectpythia.org/foundations/getting-started-jupyter).

Note, not all Cookbook chapters are executable. If you do not see
the rocket ship icon, such as on this page, you are not viewing an
executable book chapter.


### Running on Your Own Machine

If you are interested in running this material locally on your computer, you will need to follow this workflow:

(Replace "cookbook-example" with the title of your cookbooks)

1. Clone the `https://github.com/ProjectPythia/cookbook-example` repository:

   ```bash
    git clone https://github.com/ProjectPythia/cookbook-example.git
   ```

1. Move into the `cookbook-example` directory
   ```bash
   cd cookbook-example
   ```
1. Create and activate your conda environment from the `environment.yml` file
   ```bash
   conda env create -f environment.yml
   conda activate cookbook-example
   ```
1. Move into the `notebooks` directory and start up Jupyterlab
   ```bash
   cd notebooks/
   jupyter lab
   ```
