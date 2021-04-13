# NMJ_Analyser
The code was created using python 3.7 and the following version of packages
## Requirements
 - scipy 1.5.3
 - Pillow 7.2.0
 - numpy 1.19.1
 - pandas 1.1.0
 - nibabel 3.1.1
 
In addition, the following modules are imported
 - glob
 - os
 - argparse
 - sys
 - Tinker
Performs analysis of NMJ data 

## Installation
Python3 is required for NMJ-Analyser installation and won't work with Python2 

Before attempting to install NMJ-Analyser, do make sure the following packages are installed
•	SciPy, for multidimensional image processing: https://www.scipy.org/install.html
•	pillow, for reading images: https://pillow.readthedocs.io/en/stable/installation.html
•	glob, for finding the pathnames: https://docs.python.org/3/library/glob.html
•	os: https://pypi.org/project/os-sys/
•	numpy: https://numpy.org/install/
•	argparse: https://pypi.org/project/argparse/
•	pandas: https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html
•	sys: https://docs.python.org/3/install/
•	Scikit-image:https://scikit-image.org/docs/dev/install.html#install-via-pip 

With pip3 installed, type
pip3 install nmjanalyzer to install the NMJ-Analyzer package

Once the other required packages are installed, type nmj_analyzer on the command line
A window appears that will allow for the different parameters to be entered
## Usage

NMJ-Analyser requires NMJs to be separated by at least 20um. Images which contain superimposed NMJs are not ideal for analysis.
The NMJ Analyser takes as input directories where jpg or png files have been stored 

For each subject, the input is presented as 
SUBJ/*jpg or png
The ..... files must contain the keyword red or RED
The ..... files must contain the keyword green or GREEN
The slices should ordered numerically ex Mouse1_GREEN_0001.jpg.... Mouse1_GREEN_0010.jpg

The following parameters are given to the system:
 - -p regular expression of the subject path
 - -dx planar resolution
 - -dz slice thickness
 - -t threshold for voxels to be considered as positives
 
## Output
 For each subject the following parameters are calculated for each RED connected component and intersection of GREEN on RED component
 
### RegionProperties
 - 'centre of mass': (self.centre_of_mass, ['CoMx',
                                                     'CoMy',
                                                     'CoMz']),
 - 'centre_abs': (self.centre_abs, ['Truex, Truey, Truez']),
 - 'volume': (self.volume,
                       ['NVoxels', 'NVolume']),
 - 'fragmentation': (self.fragmentation, ['Fragmentation']),
 - 'mean_intensity': (self.mean_int, ['MeanIntensity']),
 - 'surface': (self.surface, ['NSurface', 'Nfaces_surf',
                                       'NSurf_ext', 'Nfaces_ext']),
 - 'surface_dil': (self.surface_dil, ['surf_dil', 'surf_ero']),
 - 'surface volume ratio': (self.sav, ['sav_dil', 'sav_ero']),
 - 'compactness': (self.compactness, ['CompactNumbDil'
                                               ]),
 - 'eigen': (self.eigen, ['eigenvalues']),
 - 'std': (self.std_values, ['std']),
 - 'quantiles': (self.quantile_values, ['quantiles']),
 - 'bounds': (self.bounds, ['bounds']),
 - 'cc': (self.connect_cc, ['N_CC']),
 - 'cc_dist': (self.dist_cc, ['MeanDistCC']),
 - 'cc_size': (self.cc_size, ['MinSize', 'MaxSize', 'MeanSize']),
 - 'max_extent': (self.max_extent, ['MaxExtent']),
 - 'shape_factor': (self.shape_factor, ['ShapeFactor',
                                                 'shapefactor_surfcount']),
 - 'skeleton_length': (self.skeleton_length, ['SkeletonLength'])
 
### Comparison Properties
 - 'green volume': (self.n_pos_ref, 'Volume_(Green)'),
 - 'red volume': (self.n_pos_seg, 'Volume_(Red)'),
 - 'n_intersection': (self.n_intersection, 'Intersection'),
 - 'n_union': (self.n_union, 'Union'),
 - 'IoU': Intersection of union
 - 'coverage': Overlap        
 - 'vol_diff': Volume difference
 - 'ave_dist': Average distance
 - 'haus_dist': Hausdorff distance
 - 'haus_dist95': 95% HD
 - 'com_dist': distance between centre of mass
 - 'com_ref': centre of mass RED
 - 'com_seg': centre of mass GREEN
