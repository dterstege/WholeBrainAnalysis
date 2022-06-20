# Whole Brain Analysis

## WholeBrainAnalysis.m

*WholebrainAnalysis.m* was developed for the compilation and analysis of datasets collected using the Whole Brain software suite developed by Daniel Fürth (https://www.wholebrainsoftware.org) and incorporates a modification using scripts and plugins developed by Dylan Terstege (https://github.com/dterstege/CavalieriPointMask).

Whole Brain is a neuroanatomical information system. Neuroanatomical data obtained from microscope images is encoded and stored in stereotactic coordinate form within the Allen Mouse Brain Atlas. The software suite can be accessed [here](https://www.wholebrainsoftware.com).

WholeBrainAnalysis.m was created by Dylan Terstege, a Neuroscience PhD candidate in the Epp Lab at the University of Calgary.


**Current Version: v1.0.2**

**New to this version:**

*Details about each update will be added here as analyses are added to the package.  Be sure to keep checking back to stay up to date.*

## Table of Contents

| Section  | Description | 
| ------------- | ------------- | 
| [0. Requirements](#req)   | What is required for running WholeBrainAnalysis.m.  |
| [1. Section 1: Initialization](#init)   | Basic data loading  |
| [2. Section 2: Regional Label Density](#dens)  | Compile data for regional density analysis  |
| [3. Section 3: Basic Network Analyses](#basic) | Very basic network analyses (more to come) |
| [4. Sections X & Y: Saving and Loading Data](#save) | information on how to save and load data structures |
| [5. Citation](#cite) | How to cite WholeBrainAnalysis.m |
| [6. Contact Us](#contact)  | Where to reach us with questions  |

<a name="req"/>

## 0. Requirements

Firstly, WholeBrainAnalysis.m was written from MATLAB.  Development utilized MATLAB R2020a.  If version-related errors should arise, please don't hesitate to contact [Dylan](#contact) for assistance.

There are several required packages which are utilized by WholeBrainAnalysis.m.  Thankfully, these packages can easily be obtained without any convoluted installation process and just need to be accessible by MATLAB.  It is preferable to have a MATLAB path folder somewhere on your system so that you don't need to copy and paste these files every time that you want to run this analysis in a new directory.

**Required packages:**
- [Brain Connectivity Toolbox](https://sites.google.com/site/bctnet/)
- [Benjamani & Hochberg False Discovery Rate](https://www.mathworks.com/matlabcentral/fileexchange/27418-fdr_bh)
- [Full WholeBrain Atlas](https://github.com/dterstege/IEGNetworkAnalyses/tree/main/requirements)
- [Custom User Atlas](https://github.com/dterstege/IEGNetworkAnalyses/tree/main/requirements/UserAtlas)

The first three of these files should remain static and not be changed from their downloaded state.

The final, the *Custom User Atlas* can be modified to best suit the desired level of analysis.  To do this, simply modify the provided user atlas with your desired regional organization. The organization of the columns (from left to right) are region ID, starting row, and end row.  These row numbers correspond with the row numbers from the Full WholeBrain Atlas file.

<a name="init"/>

## 1. Section 1: Initialization

**WholeBrainAnalysis.m runs best using section-by-section processing. It is recommended that the user uses the 'run section' command to individually run each section**

During this process, data will be loaded into the MATLAB structure element 'WB' for later use.  This step in the analysis is reasonably hands-on and requires the user to point the script to several directories and input individual animal IDs. The results of this data loading can be found under the 'inputs' element within 'WB'.

There are several variables within this section which should be adjusted for each new experiment.  Please carefully read the documentation within the MATLAB file before starting this

**INPUTS**
- "cells.csv" files: these files should contain the number of segmented LABELS per region.  This is the raw WholeBrain output from the input image with your label of interest.
- "grids.csv" files: these files should contain the number of segmented POINTS per region.  This is a raw WholeBrain output from the input image obtained using the [Cavalier Point Mask plugin](https://github.com/dterstege/CavalieriPointMask).

<a name="dens"/>

## 2. Section 2: Regional Label Density

During this process, the density of the segmented label will be calculated using a user-defined atlas organization.  This process is completely hands-off once the atlas has been created and added to the path. Its name should be inputted in the script in place of the default atlas (lines 178, 179, and 180).

**OUTPUTS**
Regional density outputs will be located in the 'outputs' element within 'WB'.  These outputs will include:
- Total region area
- Total number of segmented labels per area
- Density of the number of segmented labels per unit area

<a name="basic"/>

## 3. Section 3: Basic Network Analyses

During this process, pairwise correlation matrices will be generated by correlating the regional expression density of the segmented label across a group.  User-defined parameters will guide the network analysis.

**INPUTS**

*General Network Thresholding Details*:
- p value threshold: WB.info.networks.threshold.pthresh = 0.005
- false discovery rate threshold: WB.info.networks.threshold.fdrthresh = 0.05
- cutoff for network binarization: WB.info.networks.threshold.binary = 0.9 (this will also consider -0.9)

*Correlation Strength Survival Curve Details*: This analysis will provide details about how many correlations would meet each correlation strength threshold based on the resolution (step size) defined by the user
- minimum correlation strength to consider: WB.info.networks.corrstrength.startR = 0.00
- maximum value to consider: WB.info.networks.corrstrength.lastR = 1.00
- resolution of the analysis: WB.info.networks.corrstrength.stepSize = 0.01


**OUTPUTS**
- Correlation Matrices: PNG files saved to directory, data (including raw, p values, significant, and binary adjacency matrices) saved to 'outputs' element in 'WB'
- Circle Plots: PNG files saved to directory
- Correlation Strength Survival Vector
- Network Density
- List of Regional Degrees (sorted in same order as the Custom User Atlas)
- Global Network Efficiency
- Regional Clustering Coefficient (sorted in the same order as the Custom User Atlas)


**NOTE**: Missing regions will yield 'NaN' during pairwise correlations.  These 'Not a Number' distinctions have major implications on the results of the network analysis.  Please ensure that the only regions included in the analysis are those which you have confidently registered in WholeBrain. Relatedly, please ensure that the regions in your user atlas are present in the Allen Mouse Brain Atlas orientation that you have used in WholeBrain.  Some of the most lateral regions are only present in the coronal atlas orientation.

<a name="save"/>

## 4. Sections X & Y : Saving and Loading Data

Some of the more laborious steps, such as data initialization, are processes that you will likely not want to have to repeat.  To avoid this, I have implemented a save and load system into the analysis.  By running section X, you will save your data to the file WB.mat. By running section Y, you can load this file and the contained WB structure element.  This will allow you to tweak network parameters as you go.

Files can be renamed, so long as the name on line 396 (the load line) is adjusted accordingly.

<a name="cite"/>

## 5. Citation

If you find WholeBrainAnalysis.m to be useful, and apply it in your research, please cite the following article outlining this flexible open-source atlas registration tool:

**TEMP**

Additionally, resources from the following were also used during the development of this tool:

**Brain Connectivity Toolbox**
- Rubinov, M. & Sporns, O. (2010) Complex network measures of brain connectivity: Uses and interpretations. NeuroImage. 52(3), 1059-1069.

**fdr_bh.m**
- Benjamini, Y. & Hochberg, Y. (1995) Controlling the false discovery rate: A practical and powerful approach to multiple testing. Journal of the Royal Statistical Society, Series B (Methodological). 57(1), 289-300.


<a name="contact"/>

## 6. Contact Us

**Contributors:**
- **Dylan Terstege** (code/tool conceptualization/written documentation)
    - ![twitter-icon_16x16](https://user-images.githubusercontent.com/44174532/113163958-e3d3e400-91fd-11eb-8d79-17906d8d3f25.png)[@dterstege](https://twitter.com/dterstege) - ![Mail](https://user-images.githubusercontent.com/44174532/113164412-50e77980-91fe-11eb-9282-dd83852578ce.png)
<dylan.terstege@ucalgary.ca>

Principal Investigator:
- Jonathan Epp (tool conceptualization) 
    - https://epplab.com


