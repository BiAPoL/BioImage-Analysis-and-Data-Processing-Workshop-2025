# QM Course - Lectures on Bio-Image Analysis with napari Plugins

In these lectures, we will visualize microscopy images with [napari](https://napari.org/stable/), an nD viewer open-source software, and explore ways to analyze them with a few napari plugins.

## Course Description

This course will introduce the participants to the basics of bio-image analysis and processing in microscopy using open-source software. The course will cover the following topics:

- Installation and introduction to [napari](https://napari.org/stable/)
- Loading images from OMERO with [napari-omero](https://github.com/tlambert03/napari-omero)
- Segmentation with Machine Learning using [napari-apoc](https://github.com/haesleinhuepf/napari-accelerated-pixel-and-object-classification), [micro-sam](https://github.com/computational-cell-analytics/micro-sam and [napari-nninteractive](https://github.com/MIC-DKFZ/napari-nninteractive)
- Feature Extraction with [napari-skimage-regionprops](https://github.com/haesleinhuepf/napari-skimage-regionprops)
- Multichannel Analysis with [napari-skimage-regionprops](https://github.com/haesleinhuepf/napari-skimage-regionprops)
- Object Classification with Machine Learning using [napari-apoc](https://github.com/haesleinhuepf/napari-accelerated-pixel-and-object-classification) and [napari-clusters-plotter](https://github.com/BiAPoL/napari-clusters-plotter)

The slides can be downloaded from the [GitHub repository](https://github.com/BiAPoL/QM_Course_Bio_Image_Analysis_with_napari_2025/blob/main/Bio-Image%20Analysis%20with%20napari%20plugins.pdf)

## Setting up the environment

To follow the course, you will need to have Python installed in your computer. 

1. Follow the instruction in [this blog post](https://biapol.github.io/blog/mara_lampert/getting_started_with_miniforge_and_python/readme.html) and stop before the "Creating a virtual environment" section.

2. Open a terminal (preferably Miniforge Prompt, but not necessarily) and run the following command to clone/download the course repository to your computer:

```bash
git clone https://github.com/BiAPoL/QM_Course_Bio_Image_Analysis_with_napari_2025.git
```

Alternatively, you can download the repository as a `.zip` file by clicking on the green "Code" button on the top right of the repository page and selecting "Download ZIP". Remember the place where you decompress the file for the next steps.

3. Navigate to the course repository:

```bash
cd QM_Course_Bio_Image_Analysis_with_napari_2025
```

If you chose to download the `.zip` file in the previous step, you will need to navigate to the folder where you decompressed the file.

4. Install the required Python packages with:

```bash
mamba env create -f environment.yml
```

This creates a new environment called `napari-intro-env` and installs all the required packages.

5. Activate the environment:

```bash
mamba activate napari-intro-env
```

This will activate the environment, which means giving access to the path where the installed packages are.

You should see the name `(napari-intro-env)` now in front of the active typing line.

## Starting napari

You can now start napari by typing:

```bash
napari
```

in the terminal. The first time you start napari may take longer than usual.

