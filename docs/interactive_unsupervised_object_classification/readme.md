# Interactive unsupervised object classification in Napari

In this exercise we will perfom interactive feature plotting and manual selection, Dimensionality Reduction with [UMAP](https://umap-learn.readthedocs.io/en/latest/#) and Clustering with [HDBSCAN](https://hdbscan.readthedocs.io/en/latest/index.html) to assign objects (nuclei) to different classes in napari.
We will use the napari plugin [napari-clusters-plotter plugin](https://github.com/BiAPoL/napari-clusters-plotter?tab=readme-ov-file#napari-clusters-plotter).

## Getting started

Open a terminal window and activate your conda environment:

```
mamba activate napari25
```

Afterwards, start up Napari:

```
napari
```

Load the "BBBC007 v1" example dataset from the menu `File > Open Sample > napari clusters plotter > BBBC007 v1`. 

![](ncp1.png)

This dataset contains several images of nuclei and segmentation results with features already extracted and stored in each `Labels` layer. The dataset is from the [Broad Bioimage Benchmark Collection](https://bbbc.broadinstitute.org/BBBC007).

You should see the following layers in the napari canvas:

![](ncp2.png)

## Plotting Features in napari

Open the [napari-clusters-plotter](https://github.com/BiAPoL/napari-clusters-plotter?tab=readme-ov-file#napari-clusters-plotter) Plotter via `Layers > Visualize > Plot & select features (napari clusters plotter)`.

![](ncp3.png)

This will open a plotter. 

![](ncp4.png)

Change the features in the `x-axis` and `y-axis` dropdowns (like `area` and `mean_intensity`) to have them plotted against each other.

![](ncp5.png)

You can explore the `Avanced Options` tab to change from a scatter plot to a histogram in case there are too many points to visualize. 

![](ncp5_b.png)

For now, keep the scatter plot and go back to the `Plotting Options` tab. In the top of the plotter, you can find a few different selector buttons (`lasso`, `ellipse` and `rectangle`), a class spinbox and an eye icon to toggle the visibility of selections/clusters.

Click on the `lasso` button to have that selector enabled:

![](ncp6.png)

Now use the mouse to draw regions around some dots to have the corresponding objects highlighted in the main canvas. 

![](ncp7.gif)

The color of the selected objects in the selected layer (highlighted in blue) will change to the color of the class you have selected in the spinbox. Default is class `1` (orange).

![](ncp8.png)

If you now select all the open layers by holding `SHIFT`and clicking on the first layer and then the last one, you will add features from all layers to the plotter. You can also select individual layers by holding `CTRL` and clicking on them. If you manually select a region again, you will see that the selected objects in all layers will change to the color of the class you have selected in the spinbox.

![](ncp9.gif)

Besides manually classifying objects,, you can also change the `Hue` combobox to map a third feature to the color of the objects in the plotter. For example, you can select `eccentricity` or `perimeter` to have the color of the objects in the plotter represent these properties. *Notice that categorical features, like the `MANUAL_CLUSTER_ID`, have their background always highlighted.*

![](ncp10.gif)

Close the plotter.

### Dimensionality Reduction

Apply UMAP to have all these dimensions reduced to 2. Do this via `Tools > Measurement post-processing > Dimensionality reduction (ncp)`. 

Choose `UMAP` under `Dimensionality Reduction Method`.  Select all measurements (while holding `SHIFT`, click on the first one, scroll down to the last one and then click on the last one). Click on `Run`.

![](ncp11.png)

After some time, the table should pop-up again with new columns (`UMAP-0` and `UMAP-1`). Feel free to close the table and the dimensionality reduction widget.

![](ncp12.png)

### Clustering

Apply HDBSCAN clustering by first opening the clustering widget via `Tools > Measurement post-processing > Clustering (ncp)`. Select **only** `UMAP-0` and `UMAP-1` now in `Measurements` (hold `CRTL` while clicking on them). Under `Clustering Method` choose `HDBSCAN` and click on `Run`

![](ncp13.png)

The table should pop-up yet again with a new `HDBSCAN_CLUSTER_ID` column. Feel free to close it.

### Visualize Object Classification Results

Open the plotter again, under `Axes` choose `UMAP-0` and `UMAP-1` and under `Clustering` choose `HDBSCAN_CLUSTER_ID`. Click on `Plot`. Try to infer why these classes were classified differently (hide and show layers or turn grid mode on to better inspect results).

![](ncp14.png)

Without any ground-truth provided, we just assigned objects to different classes based on some features relationships. We just perfomed an unsupervised machine learning workflow!