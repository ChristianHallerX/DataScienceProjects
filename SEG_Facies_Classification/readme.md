# Sedimentary Facies Machine Learning - XGBoost with Intelligent Bayesian Optimization

<a href="https://christianhallerx.github.io/research/2020-09-07-ML_Facies/" target="_blank">Read full text on website.</a><br>

The Society of Exploration Geophysicists (SEG), Matt Hall (Agile), and Brendon Hall (Enthought) ran in 2016 a **competition** on who can create the best Machine Learning model in classifying sedimentary facies in several wells using wireline measurements. For the dataset provided, a **subject-matter expert** (e.g., sedimentologist) manually described core sections and gave the facies names, which is calles labeling. This complete dataset can be used to train a Machine Learning Model. Note that in Artificial Intelligence rules are not hard-coded as in traditional programming, rather we give the computer the inputs and outputs, and the let it figure out the rules. These rules can then be used to make predictions on new, unseen, data. In this case we can then use new wireline data to predict sedimentological facies.

The dataset, along with instructions were made available online in an article in SEG The Leading Edge <a href="https://library.seg.org/doi/10.1190/tle35100906.1" target="_blank">"Facies classification using machine learning"</a>. The article included a link to <a href="https://github.com/seg/2016-ml-contest/blob/master/Facies_classification.ipynb" target="_blank">some starter code in a Jupyter notebook</a> with a simple Support Vector Machine model that had to be surpassed in accuracy.

In 2017, the results of the SEG competition were published in the <a href="https://doi.org/10.1190/tle36030267.1" target="_blank">SEG Leading Edge journal</a> including <a href="https://github.com/seg/2016-ml-contest" target="_blank">all submission files</a> for contestants to learn from each other. Teams were allowed to send new and improved models.

![](https://raw.githubusercontent.com/ChristianHallerX/DataScienceProjects/master/SEG_Facies_Classification/STUART_comparison.png)
