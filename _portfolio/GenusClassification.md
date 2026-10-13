---
title: "Genus Classification of LIDAR Tree Canopy"
collection: portfolio
---

Developed a pipeline for segmenting tree objects (or "shapes") from LIDAR of urban canopy cover, then training a Random Forest model to classify between 25 genera.

Two-level classification:
<ul>
  <li>Pixel-level: Each pixel at 7 inch resolution was classified with a probability across 25 genera.</li>
  <li>Canopy-level: Every pixel within each tree object is aggregated to choose the Genus for the tree.</li>
  <li>Preliminary pixel-level accuracy reached 61.17% showing room for potential!</li>
</ul>

<figure>
  <img src="{{ '/images/GenusClassification/segmentation.png' | relative_url }}" alt="Segmentation">
  <figcaption>Excerpt of the segmentation process, tweaking shape generation parameters to better segment tree objects.</figcaption>
</figure>


<figure>
  <img src="{{ '/images/GenusClassification/WyandotteLAI.png' | relative_url }}" alt="Wyandotte LAI">
  <figcaption>Image of the raw LAI which was used for different segmentation and classification methods.</figcaption>
</figure>


The project consisted of three main steps in the pipeline:

<ol>
  <li>Tree segmentation: Converting raw flyover LIDAR data into tree top points and then segmented tree objects.</li>
  <li>Data Preparation: Engineering features using multi-spectral data ratios and structural metrics from the LIDAR to assist in classification.</li>
  <li>Model Creation: Hyperparameter tuning Random Forest models and engineering new features based on variables with the most importance to increase model performance and prunce irrelevant features.</li>
</ol>

This project had nearly 1300 tree records, with the most recent dataset being 2million pixel records~ by 343 features. This amount of data required the usage of specific packages to speed up calculations and designed batching to maintain enough memory for the full pipeline.

<figure>
  <img src="{{ '/images/GenusClassification/Helper Functions.PNG' | relative_url }}" alt="Helper Functions">
  <figcaption>Helper functions created to automate model training runs, VIF and importance filtering, and logging across different hyperparameter configurations.</figcaption>
</figure>


<figure>
  <img src="{{ '/images/GenusClassification/Log.PNG' | relative_url }}" alt="Training Log">
  <figcaption>Example output from the automated training log, recording accuracy metrics, training time, hyperparameters, and selected features for each run.</figcaption>
</figure>
