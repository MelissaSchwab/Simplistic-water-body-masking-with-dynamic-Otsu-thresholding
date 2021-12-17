# Simplistic-water-body-masking-with-dynamic-Otsu-thresholding

## Abstract
The accurate description of the abundance and geometry of lakes is critical for many environmental applications. Here, hyperspectral Airborne Visible/Infrared Imaging Spectrometer – Next Generation (AVIRIS-NG) imagery was captured over the Arctic Mackenzie Delta and assessed for its efficiency to accurately classify open water bodies. Our surface water mask approach comprises the computation of several common single- and multi-band water indices, the removal of noise effects, the interpolation of missing values, and adaptive Otsu thresholding maximizing inter-class variance. Accuracy was evaluated using an independent and complimentary water mask derived from AirSWOT color-infrared imagery. Overall accuracies and kappa coefficients of the resulting high-resolution masks display values higher than 0.89. Although the Single-Band Short-Wave Infrared (SWIR) and the Multi-Band Water Index (MBWI) are more efficient in detecting minor open water bodies, we note an increase in commission errors resulting in lower overall accuracies. The Modified Normalized Difference Water Index (MNDWI) robustly discriminates surface water from confused backgrounds and faithfully reproduces the AirSWOT reference mask. These preliminary investigations provide a baseline for more sophisticated water classification workflows.

## Introduction
The accurate mapping of terrestrial surface water bodies is essential for the research, monitoring, and management of freshwater resources. Remote sensing technology provides spatially explicit and temporally frequent optical data allowing the continuous observation of water geometry and dynamics at multiple scales. However, open water detection via non-commercial, space-borne remote sensors is often restricted by medium and coarse spatial resolution (30 – 1000 m) limiting observable lake sizes to 2000 m<sup>2</sup> or larger<sup>[1]</sup>. Arctic-Boreal regions, consisting of extensive lake and wetland areas<sup>[1,2]</sup>, are strongly susceptible to climate variability, the presence of permafrost, and surface-groundwater interaction, resulting in permanent lake size fluctuations<sup>[3,4]</sup>. High-resolution water surface maps are crucial to correctly quantify changes in water volume and associated biogeochemical processes. Surface water extraction methods often rely on spectral water indices. Optical water masking approaches leverage the strong light absorption of water in the Near-Infrared (NIR) and Short-Wave Infrared (SWIR) bands, including the Normalized Difference Water Index (NDWI)<sup>[5]</sup>, the Modified Normalized Difference Water Index (MNDWI)<sup>[6]</sup>, and the Multi-Band Water Index (MBWI)<sup>[7]</sup>. These multi-band indices attempt to maximize the spectral variance between water and non-water features. Here, we explore and evaluate the performance of single- and multi-band surface water indices to classify open water areas derived from hyperspectral imagery. These high-resolution images featuring the Outer Delta of the Arctic Mackenzie River were derived from the Airborne Visible/Infrared Imaging Spectrometer – Next Generation (AVIRIS-NG) as part of the Arctic-Boreal Vulnerability Experiment (ABoVE) in 2017. 

## Materials & Methods
AVIRIS-NG hyperspectral data was collected over the Outer Mackenzie Delta during the field campaign in August 20178. The push-broom imaging spectrometer measures reflected solar radiance in the visible to shortwave infrared spectral range (380 to 2510 nm) at 5 nm intervals with a spatial resolution of 5.1 m. Cloud-free reflectance imagery of 27 individual flight lines, spanning ca. 5080 km<sup>2</sup>, was orthorectified and atmospherically corrected using a bidirectional reflectance distribution function<sup>[9]</sup>. We calculated four commonly used water indices (Table 1) including a SWIR single-band index (2220 nm), the NDWI<sup>[5]</sup>, the MNDWI<sup>[6]</sup>, and the MBWI<sup>[7]</sup>. Missing values, errors, and outliers (e.g., dark vegetated areas) were identified, removed, and replaced with values obtained from nearest-neighbor interpolation. Spectral water indices often rely on a constant threshold value of 0.0 to generate binary masks. However, depending on different image and water characteristics, optimal threshold values can vary both temporally and spatially. Dynamically selected thresholds are applied to individual images achieving a more accurate delineation of water bodies. The Otsu algorithm<sup>[10]</sup> is a non-parametric threshold detection method improving interclass variances. Otsu’s method reaches its highest performance when the two populations are equivalent. Given the abundance of open water features in the Mackenzie Delta, land and water pixels approach a balanced bimodal distribution. To test and validate the extracted masks, we selected the open water mask derived from the airborne AirSWOT instrument suite of the upcoming Surface Water Topography Mission as a reference dataset<sup>[11]</sup>. AirSWOT was deployed to the Mackenzie Delta in August 2017, simultaneously to AVIRIS-NG, and overlaps with the flight line ang20170809t211931 located in the Upper MackenzieDelta. AirSWOT consists of an interferometric Ka-band synthetic aperture radar and a color-infrared (CIR) camera. A semi-automated, object-oriented water classification algorithm building on the NDWI was applied to compute a high resolution (1 m) surface water mask. Detected water body sizes range from 40 m<sup>2</sup> to 15 km<sup>2</sup>. The AirSWOT water mask was rasterized and a pixel-based confusion matrix was calculated to quantify classification errors. The total error is defined as the sum of commission and omission errors. Errors of commission refer to the incorrect classification of non-water pixels, while errors of omission occur when the model fails to correctly identify water pixels. Geospatial data manipulation, Otsu-based thresholding, and accuracy evaluation were performed in the Python v3.8 programming language using the GDAL12 and SciKit Image<sup>[13]</sup> libraries.

![Methodology flowchart](https://github.com/MelissaSchwab/Simplistic-water-body-masking-with-dynamic-Otsu-thresholding/blob/main/images/Methodology%20flowchart.png)

## References
[1] Verpoorter, C., Kutser, T., Seekell, D. A. & Tranvik, L. J. A global inventory of lakes based on high-resolution satellite imagery. Geophys. Res. Lett. 41, 6396–6402 (2014).   
[2] Pekel, J. F., Cottam, A., Gorelick, N. & Belward, A. S. High-resolution mapping of global surface water and its long-term changes. Nature 540, 418–422 (2016).   
[3] Carroll, M., Wooten, M., DiMiceli, C., Sohlberg, R. & Kelly, M. Quantifying surface water dynamics at 30 meter spatial resolution in the North American high northern latitudes 1991-2011. Remote Sens. 8, (2016).   
[4] Cooley, S. W., Smith, L. C., Ryan, J. C., Pitcher, L. H. & Pavelsky, T. M. Arctic-Boreal Lake Dynamics Revealed Using CubeSat Imagery. Geophys. Res. Lett. 46, 2111–2120 (2019).   
[5] McFeeters, S. K. The use of the Normalized Difference Water Index (NDWI) in the delineation of open water features. Int. J. Remote Sens. 17, 1425–1432 (1996).   
[6] Xu, H. Modification of normalised difference water index (NDWI) to enhance open water features in remotely sensed imagery. Int. J. Remote Sens. 27, 3025–3033 (2006).      
[7] Wang, X. et al. A robust Multi-Band Water Index (MBWI) for automated extraction of surface water from Landsat 8 OLI imagery. Int. J. Appl. Earth Obs. Geoinf. 68, 73–91 (2018).    
[8] Miller, C. E. et al. An overview of above airborne campaign data acquisitions and science opportunities. Environ. Res. Lett. 14, (2019).     
[9] Greenberg, E. et al. Combined Sun Glint and Vegetation BRDF Correction over Heterogeneous Wetland Land Cover. In prep.     
[10] Otsu, N. A Threshold Selection Method from Gray-Level Histograms. IEE Trans. Syst. Man, Cybern. 9, 62–66 (1979).     
[11] Kyzivat, E. D. et al. A high-resolution airborne color-infrared camera water mask for the NASA ABoVE campaign. Remote Sens. 11, (2019).     
[12] Warmerdam, F., Rouault, E. & Others. GDAL Documentation. (2021).     
[13] Van Der Walt, S. et al. Scikit-image: Image processing in python. PeerJ 2014, (2014).    
