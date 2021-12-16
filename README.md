# Simplistic-water-body-masking-with-dynamic-Otsu-thresholding

## Abstract
The accurate description of the abundance and geometry of lakes is critical for many environmental applications. Here, hyperspectral Airborne Visible/Infrared 
Imaging Spectrometer – Next Generation (AVIRIS-NG) imagery was captured over the Arctic Mackenzie Delta and assessed for its efficiency to accurately classify 
open water bodies. Our surface water mask approach comprises the computation of several common single- and multi-band water indices, the removal of noise effects, 
the interpolation of missing values, and adaptive Otsu thresholding maximizing inter-class variance. Accuracy was evaluated using an independent and complimentary 
water mask derived from AirSWOT color-infrared imagery. Overall accuracies and kappa coefficients of the resulting high-resolution masks display values higher 
than 0.89. Although the Single-Band Short-Wave Infrared (SWIR) and the Multi-Band Water Index (MBWI) are more efficient in detecting minor open water bodies, we 
note an increase in commission errors resulting in lower overall accuracies. The Modified Normalized Difference Water Index (MNDWI) robustly discriminates surface 
water from confused backgrounds and faithfully reproduces the AirSWOT reference mask. These preliminary investigations provide a 	baseline for more sophisticated 
water classification workflows.

## Introduction
The accurate mapping of terrestrial surface water bodies is essential for the research, monitoring, and management of freshwater resources. Remote sensing 
technology provides spatially explicit and temporally frequent optical data allowing the continuous observation of water geometry and dynamics at multiple 
scales. However, open water detection via non-commercial, space-borne remote sensors is often restricted by medium and coarse spatial resolution (30 – 1000 m) 
limiting observable lake sizes to 2000 m2 or larger1. Arctic-Boreal regions, consisting of extensive lake and wetland areas1,2, are strongly susceptible to 
climate variability, the presence of permafrost, and surface-groundwater interaction, resulting in permanent lake size fluctuations3,4. High-resolution water 
surface maps are crucial to correctly quantify changes in water volume and associated biogeochemical processes. Surface water extraction methods often rely on 
spectral water indices. Optical water masking approaches leverage the strong light absorption of water in the Near-Infrared (NIR) and Short-Wave Infrared (SWIR) 
bands, including the Normalized Difference Water Index (NDWI)5, the Modified Normalized Difference Water Index (MNDWI)6, and the Multi-Band Water Index (MBWI)7. 
These multi-band indices attempt to maximize the spectral variance between water and non-water features. Here, we explore and evaluate the performance of single- 
and multi-band surface water indices to classify open water areas derived from hyperspectral imagery. These high-resolution images featuring the Outer Delta of 
the Arctic Mackenzie River were derived from the Airborne Visible/Infrared Imaging Spectrometer – Next Generation (AVIRIS-NG) as part of the Arctic-Boreal 
Vulnerability Experiment (ABoVE) in 2017. 
