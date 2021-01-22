# Equinor_Volve_LogML

This repository is my exploration on bringing machine learning to "Volve" oil field open dataset disclosed to the public by Equinor since 2018. For more information about this dataset and how to access the original database, see [here](https://www.equinor.com/en/how-and-why/digitalisation-in-our-dna/volve-field-data-village-download.html).

## Background
> The Volve field in the Norwegian North Sea: 2008—2016. 
> The Volve oil field, located 200 kilometres west of Stavanger at the southern end of the Norwegian sector, was decommissioned in September 2016 after 8.5 years in operation, more than twice as long as originally planned. 
> The development was based on production from the Mærsk Inspirer jack-up rig, with Navion Saga used as a storage ship to hold crude oil before export. Gas was piped to the Sleipner A platform for final processing and export. Volve reached a recovery rate of 54% and in March 2016 the licence decided to shut down its production permanently. The field was originally scheduled for 3-5 years of operation.
> https://www.equinor.com/en/what-we-do/norwegian-continental-shelf-platforms/volve.html

## Data:

- Depth [m] Below Surface
- NPHI [vol/vol] Neutron Porosity (not not calibrated in basic physical units) <a href="https://www.glossary.oilfield.slb.com/en/terms/n/neutron_porosity" target="_blank">Reference</a>
- RHOB [g/cm3] Bulk Density. <a href="https://www.sciencedirect.com/topics/engineering/density-log" target="_blank">Reference</a> 
- GR [API] Gamma Ray radioactive decay (aka shalyness log). <a href="https://www.glossary.oilfield.slb.com/en/terms/g/gamma_ray_log" target="_blank">Reference</a> 
- RT [ohm*m] Resistivity True. <a href="https://www.glossary.oilfield.slb.com/en/terms/r/resistivity_log" target="_blank">Reference</a> 
- PEF [barns/electron] PhotoElectric absorption Factor. <a href="https://www.glossary.oilfield.slb.com/en/Terms/p/pef.aspx" target="_blank">Reference</a>
- CALI [inches] Caliper = Borehole Diameter. <a href="https://www.glossary.oilfield.slb.com/en/terms/c/caliper_log" target="_blank">Reference</a>
- DT [μs/ft] Delta Time, Sonic Log, P-wave, interval transit time. <a href="https://en.wikipedia.org/wiki/Sonic_logging" target="_blank">Reference</a>

## Goal:

Wells 15/9-F-11B and 15/9-F-1C have no DT Sonic Log feature.
Predict Sonic Log (DT)in these two wells.


## Workflow

* Well 15/9-F-11A, 15/9-F-11A, and 15/9-F-1B are used as training data.
* The training data are normalized using Yeo-Johnson method of power transformation, and outliers have been removed using One-Class SVM method.
* Regressors in *Scikit-Learn* used are: Linear Regression, Random Forest, Support Vector Machine, Decision Tree, Gradient Boosting, and K-Nearest Neighbors.
* Best performance achieved by Gradient Boosting.
* Hyperparameter tuning showed the best hyperparameter of GB as follows; `n_estimators`=1,000 and `max_depth`=100
* Average R² and RMSE score achieved are .95 and .12 

**Result:**

The predicted results are written in CSV files; well [15/9-F-11B](https://github.com/yohanesnuwara/volve-machine-learning/blob/main/results/15_9-F-11B_Predicted_DT.csv) and [15/9-F-1](https://github.com/yohanesnuwara/volve-machine-learning/blob/main/results/15_9-F-1C_Predicted_DT.csv)

![final-well2](https://user-images.githubusercontent.com/51282928/96087823-aea53500-0eee-11eb-869f-594ff579d528.png)
