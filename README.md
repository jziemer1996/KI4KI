# KI4KI - Künstliche Intelligenz für klimaresilientes Infrastrukturmonitoring  
## Artificial Intelligence for Climate-resilient Infrastructure Monitoring


This repository summarizes the main findings and reserach contributions of the KI4KI project between the Friedrich Schiller University Jena and the Ruhrverband. KI4KI was funded between 2022 and 2025 as a BMWK (Federal Ministry for Economic Affairs and Climate Action) joint project and delt with the development of AI-based approaches in multi-temporal interferometric aperture radar (MT-InSAR) time series for the monitoring of dam deformations in Germany. 

<p align="center" width="100%">
    <img src="imgs/KI4KI.jpg" width="600" alt="Image of KI4KI"> 
</p>

## Table of Contents

- [Background](#background)
- [Structure](#structure)
- [Programming](#programming)
- [License](#license)
- [Associates](#associates)
- [Acknowledgements](#acknowledgements)

## Background

Dams are critical infrastructure with high socio-economic and environmental importance, whose structural integrity must be ensured over long operational lifetimes. Continuous monitoring is essential to detect slow, progressive deformations that may indicate material fatigue, foundation instability, or changing loading conditions. In the context of climate change, area-wide monitoring of critical infrastructure is becoming increasingly important, as more frequent and intense extreme weather events can impose additional hydraulic and mechanical stresses on dam structures and their foundations. MT-InSAR provides a unique capability to measure millimeter-scale surface deformations over large areas with high spatial density and long temporal coverage, complementing conventional in-situ instrumentation. Therefore, KI4KI focused on the analysis and prediction of dam deformations in Germany using satellite-based methods such as the Persistent Scatterer Interferometry (PSI). This repository provides the general findings of our research.

For more information about the project, please also refer to:
- [KI4KI @FSU Jena](https://www.chemgeo.uni-jena.de/30371/infrastrukturueberwachung-mit-radarinterferometrie)
- [KI4KI @Ruhrverband](https://ruhrverband.de/en/sustainability/research-projects/current-projects/ki4ki)
- [KI4KI @EOlab](https://eo-lab.org/de/projects/)

## Structure

<p align="center" width="100%">
    <img src="imgs/Schaubild_KI4KI.jpg" width="600" alt="Image of Schaubild_KI4KI"> 
</p>

#### 1) [Feasibility Assessment](results/1_Feasibility_Assessment/README.md)
We first assessed the feasibility of MT-InSAR data for operational dam monitoring by comparing the satellite-based deformations to in situ time series. For this purpose, freely available MT-InSAR data from the German Ground Motion Service (BBD) were used as analysis-ready datasets (ARD).
##### Related Publications:
- [Assessing the Feasibility of Persistent Scatterer Data for Operational Dam Monitoring in Germany: A Case Study](https://www.mdpi.com/2072-4292/17/7/1202)
- [Evaluating the German Ground Motion Service for Operational Dam Monitoring: A Comparison of InSAR Data with In Situ Measurements](https://www.mdpi.com/2072-4292/17/21/3649)
- [Dam Monitoring With Ground Motion Services–A Case Study of a Gravity Dam with the German Ground Motion Service](https://ieeexplore.ieee.org/abstract/document/10641662)
  
#### 2) [Sensor Fusion](results/2_Sensor_Fusion/README.md)
Second, we combined SAR data from different sensors (Sentinel-1 C-band and TerraSAR-X X-band) to leverage the high spatial resolution of TSX with the wide coverage of S-1. Based on the combined MT-InSAR time series, we then identified the drivers for dam deformation using in situ pendulum data for comparison. 
##### Related Publications:
- [Identifying Deformation Drivers in Dam Segments Using Combined X-and C-Band PS Time Series](https://www.mdpi.com/2072-4292/17/15/2629)
  
#### 3) [Deformation Prediciton](results/3_Deformation_Prediction/README.md)
Further, a strategy was developed to not only analyze recent deformation patterns but also to predict the future deformation behavior of dams. Traditional methods (i.e., linear regression models) were therefore enhanced by employing data-driven techniques and integrating S-1 PS time series alongside in situ data.
##### Related Publications:
- [Enhancing the Prediction of Dam Deformations: A Novel Data-Driven Approach](https://www.mdpi.com/2072-4292/17/6/1026)
- [Data-Driven Prediction of Large Infrastructure Movements Through Persistent Scatterer Time Series Modeling](https://ieeexplore.ieee.org/document/10642253)
  
#### 4) [ECR Analysis & Sidelobe Suppression](results/4_ECR_Analysis/README.md)
To enable the monitoring of dams with poor conditions for a PS-based monitoring strategy, electronic corner reflectors (ECRs) were installed at various dams. Additionally, a methodology was developed to minimize strong side lobes in the ECR-PS time series.
##### Related Publications:
- [Towards Operational Dam Monitoring with PS-InSAR and Electronic Corner Reflectors](https://www.mdpi.com/2072-4292/17/7/1318)
- [Enhancing Dam Monitoring: Utilizing the CR-Index for Electronic Corner Reflector (ECR) Site Selection and PSI Analysis](https://ieeexplore.ieee.org/document/10640447)
- [First Assessment of Electronic Corner Reflectors for Dam Monitoring in Germany](https://lps25.esa.int/lps25-presentations/poster/First%20Assessment%20of%20Electronic%20Corner%20Reflectors%20for%20Dam%20Monitoring%20in%20Germany.pdf)
- [Novel Amplitude-based Approach for Reducing Sidelobes in Persistent Scatterer Interferometry Processing using Spatially Variant Apodization](https://www.mdpi.com/1424-8220/26/1/204)
  
#### 5) [Application Programming Interface](results/5_API/README.md)
Finally, to enable dam operators to access the PS time series, an API was developed that includes both the feasibility assessments for a PS-based monitoring strategy and the processed ECR time series with a length of up to two years.
##### Related Publications:
- An Integrated Monitoring Concept for Dam Infrastructure: Operational PSI Service and Application of Electronic Corner Reflectors (ECR) (submitted)


## Programming
The following software packages were developed as part of KI4KI or are associated with version updates of existing packages:

#### 1) [TSX2StaMPS](https://github.com/jziemer1996/TSX2StaMPS)
This software allows for the semi-automatic generation of single-master interferogram stacks using high-resolution TSX Stripmap data in ESA's SNAP software. The output files can be ingested into StaMPS for PSI processing.  
#### 2) [Snap2StaMPSv2](https://github.com/mdelgadoblasco/snap2stamps/tree/v2.0.1)
Snap2StaMPSv2 represents a further development of the original Snap2StaMPS, extending its functionality to include TSX Stripmap data. The updated version therefore presents both TSX2StaMPS and the original version of Snap2Stamps as a single new package to handle the preprocessing of either TSX or S-1 data for ingestion into StaMPS.  
#### 3) [Dam2Predict](https://github.com/Gideon-Stein/KI4KI/tree/main)
This repository provides tools for forecasting dam deformations based on environmental drivers using PSI data and pendulum time series.  
#### 4) [SVA-with-Snappy](https://github.com/natasnat/SVA-with-snappy)
This package introduces an amplitude-based method that applies Spatially Variant Apodization (SVA) to reduce sidelobes in Synthetic Aperture Radar (SAR) data.  

## License

This project is licensed under the [MIT LICENSE](https://opensource.org/license/mit).

## Associates
#### - Leadership: Department for Earth Observation, Friedrich Schiller University, Jena ([JEOS JENA](https://www.chemgeo.uni-jena.de/29150/fernerkundung))

- Computer Vision Group Jena, Friedrich Schiller University, Jena ([CVG JENA](https://inf-cv.uni-jena.de/))
- German Federal Institute for Geosciences and Natural Resources (BGR), Hannover
- Ruhrverband (Association for Water Management), Essen
- Thüringer Fernwasserversorgung (TFW), Erfurt

## Acknowledgements
We acknowledge financial support through DLR with funds provided by the Federal Ministry for Economic Affairs and Climate Action (BMWK) due to an enactment of the German Bundestag under Grant No. **50EE2202A**.
