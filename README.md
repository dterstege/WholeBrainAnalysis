# Whole Brain Analysis

## WholeBrainAnalysis.m

*WholebrainAnalysis.m* was developed for the compilation and analysis of datasets collected using the Whole Brain software suite developed by Daniel Fürth (https://www.wholebrainsoftware.org) and incorporates a modification using scripts and plugins developed by Dylan Terstege (https://github.com/dterstege/CavalieriPointMask).

Whole Brain is a neuroanatomical information system. Neuroanatomical data obtained from microscope images is encoded and stored in stereotactic coordinate form within the Allen Mouse Brain Atlas. The software suite can be accessed [here](https://www.wholebrainsoftware.com).

WholeBrainAnalysis.m was created by Dylan Terstege, a Neuroscience PhD candidate in the Epp Lab at the University of Calgary.


**Current Version: v1.0.2**

**New to this version:**

Details about each update will be added here as analyses are added to the package.  Be sure to keep checking back to stay up to date.

## Table of Contents

| Section  | Description | 
| ------------- | ------------- | 
| [0. Requirements](#req)   | What is required for running WholeBrainAnalysis.m.  |
| [1. Section 1: Initialization](#init)   | Basic data loading  |
| [2. Section 2: Regional Label Density](#dens)  | Compile data for regional density analysis  |
| [3. Section 3: Basic Network Analyses](#basic) | Very basic network analyses (more to be added soon...) |
| [4. Citation](#cite) | How to cite WholeBrainAnalysis.m |
| [5. Contact Us](#contact)  | Where to reach us with questions  |

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

temp

<a name="dens"/>

## 2. Section 2: Regional Label Density

temp

<a name="basic"/>

## 3. Section 3: Basic Network Analyses

temp

<a name="cite"/>

## 4. Citation

If you find WholeBrainAnalysis.m to be useful, and apply it in your research, please cite the following article outlining this flexible open-source atlas registration tool:

**TEMP**

Additionally, resources from the following were also used during the development of this tool:

**Brain Connectivity Toolbox**
- Rubinov, M. & Sporns, O. (2010) Complex network measures of brain connectivity: Uses and interpretations. NeuroImage. 52(3), 1059-1069.

**fdr_bh.m**
- Benjamini, Y. & Hochberg, Y. (1995) Controlling the false discovery rate: A practical and powerful approach to multiple testing. Journal of the Royal Statistical Society, Series B (Methodological). 57(1), 289-300.


<a name="contact"/>

## 5. Contact Us

**Contributors:**
- **Dylan Terstege** (code/tool conceptualization/written documentation)
    - ![twitter-icon_16x16](https://user-images.githubusercontent.com/44174532/113163958-e3d3e400-91fd-11eb-8d79-17906d8d3f25.png)[@dterstege](https://twitter.com/dterstege) - ![Mail](https://user-images.githubusercontent.com/44174532/113164412-50e77980-91fe-11eb-9282-dd83852578ce.png)
<dylan.terstege@ucalgary.ca>

Principal Investigator:
- Jonathan Epp (tool conceptualization) 
    - https://epplab.com


