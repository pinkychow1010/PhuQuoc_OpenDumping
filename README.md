# PhuQuoc_OpenDumping
A Google Earth Engine script for Dumping Site Detection on Phu Quoc Island, Vietnam Using Sentinel 2

## Objective:

This Google Earth Engine script aims to detect open dumping sites on Phu Quoc Island, Vietnam to analysis 
their methane emission and potential leaching impacts.

## Research Questions:

1) Can open dumping sites on Phu Quoc can be detected using optical remote sensing data such as Sentinel 2?
2) What are the temporal patterns of methane emission from the open dumping sites on Phu Quoc?

## Workflow:
 
This script have fulfilled several task: First, it use the ground truth data to detect dumping sites
after visual inspection and preprocessing of the data. The classification is two-fold:
First, it use the spectral bands, as well as Tasseled Cap Analysis to classify different land use surface, with barren land assigned 
as potential sites for illegal dumping. Secondly, the barren land is further processed with another
binary classification into dumping sites and non-dumping sites. Instead of spectral bands, it uses 
indices such as NDVI, methane proxy and land surface temperature which is revealed as useful indices
in the existig literature. The methane proxy can be divided into Multi-band–single-pass (MBSP) retrieval
and adapted Single-band–multi-pass (SBMP) retrieval, which are proposaled in recent literature to 
estimate methane emission using band 11 and 12 of the Sentinel-2 data. Both results are compared.
Finally, a time series analysis of methane proxy at the dumping sits is implemented, to investigate
the temporal patterns of methane emission compared to other land use class.

## Results:
 
The classification of land use in the first step have achieved overall 98.5% accuracy, yet this
exceptionally high value are owing to the dominant sample from the forest and water class. 
The accuracy for each land use class are all fairly satistfactory, ranging from 71.1% to 99.9%,
with lowest classification accuracy for the barren land, due to the confision with the forest/ vegetation class.
 
As the spectral signature between barren land and dumping sites are highly similar, the second fold
classification cannot achieved a satistfactory results, as the values of the proxies from the training
sample are highly heterogenous. This might duw to a different nature of the landfill, such as for construction
waste or for organic waste. The dumping sites either has higher LST or lower LST than the barren land,
the same is for the methane proxy. Secondly, the training sample of the dumping sites are very limited in 
in the data point of view, with 5 polygons with limited size. It added up the difficulty for high accuracy.
From the results, both the highest LST and methane proxy coming from the barren land rather than the 
dumping sites. However, the temporal patterns of methane emission from barren land and dumping sites seem
to be different compared to other land uses, yet more investigation in this direction is needed. 

## Output:
 
1) A model for two-fold land use classification and detection of open dumping sites
2) Accuracy assessment for land use classification
3) Calculation of methane proxies and land surface temperature at the potential dumpings sites
4) Object-based potential dumpsites filtering based on object size
5) Google Earth App User Interface for the classification results
 
## Applications:

1) Using Sentinel-2 to map methane emission at a much higher resolution (10m x 10m) compared to Sentinel-5P (5.5 km x 3.5 km)
   which is also unavailable in this area.
2) Hierarchical classification to enhance accuracy for detecting barren land and potential dumping sites (Overall Classification Accuracy 98.5%).

## Limitations:
 
1) Confusion between barren land, sandy arreas, harvasted agricultural field, construction sites and open dumping sites
2) Limited accuracy for mixed pixels
3) Influences from methane emission at wetlands
4) Uncertainty of methane proxies
5) Training data hardly transferable to other dumping sites compared to other land use class, possibly due to heterogenity of the class
   For example, open dumping ground in Mumbai, India cannot be trained for existing dumping ground on Phu Quoc Island,
   although all other land use classes can be easily transfered (eg, forest, water).
6) Limited training data available compared to other land cover class
 
## Conclusion:
    
1) Two-layered hierarchical classification, land use classification followed by binary classification has offered 
   high potential to enhance detection of dumping sites compared to single classification.
2) Dumping sites do not display homogenous LST / methane proxy patterns to be distinguished from barren land.
3) Transferring dumping sites from other regions has not noticeably enhance the detection accuracy.
4) Methane proxy at dumping sites are remarkably lower than at the construction sites but higher than other barren land.
5) Adapted SBMP, compared to MBSP or LST, has shown a better potential in dumping site detection.
 
## Future Effort Needed:
 
1) Investigate impacts of urban areas on methane proxy
2) Study on temporal patterns of methane emission at the dumping sites
3) Model for obtaining absolute methane emission quantity from the proxy values
4) Study on spectral characteristics of dumping sites' heterogenity (eg. organic waste versus construction waste)
5) Develop pre-trianed model covering heterogenous open dumping ground of all types

## References:
 
Kashyap, P., &amp; Borongan, G. (2018). (rep.). Country Profile Viet Nam: 
    Managing municipal solid waste and packaging waste. Bonn: Deutsche Gesellschaft für Internationale Zusammenarbeit (GIZ) GmbH. 
Varon, D. J. et. al.(2021). High-frequency monitoring of anomalous methane 
    point sources with multispectral Sentinel-2 satellite observations. Atmospheric Measurement Techniques, 14(4), 2771-2785.
