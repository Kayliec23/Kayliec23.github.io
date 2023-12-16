## My Project

I applied machine learning techniques to investigate... Below is my report.

***

## Introduction

In this study we will use the Palmer penguin dataset from the UCI Machine Learning Repository to evaluate and compare logistic regression model with Multi-Layer Perceptron (MLP) Classifier Neural Network. The purpose of this study is to compare the performance of the two models for binary classification as well as multi-classification. To do this we will examine three sets of outcomes: penguin species, geographical location of the penguins, and penguin sex. The first two outcomes can be classified into three classes, whereas the last into two.

We concluded that overall the MLP Classifier NN performs better than the classical logitsic regression model, however, both show the best results for the "species" class. 

## Data

The data for this study was collected from penguins nesting on three islands within the Palmer Archipelago (Biscoe, Torgersen and Dream), near Anvers Island, Antarctica. The data was collected during three austral summers between 2007-2010, during the penguins nesting time. This field work collected data from three penguin species: the Adelie, Chinstrap and Gentoo.  

![](assets/IMG/pie.png)

*Figure 1: Distrubtion of the three different penguin species exmained in this data: Adelie, Gentoo, and Chinstrap.*

![](assets/IMG/pie_island.png)

*Figure 2: Distrubtion of the three different islands where penguin data was collected from: Biscoe, Torgersen, and Dream.*

![](assets/IMG/pie_sex.png)

*Figure 3: Distrubtion of the two penguin sexes exmained in this data: male and female.*

Overall 344 samples were taken, and data was collected of nine different features: species, region, island, individual IDs, nesting stage, clutch completion, egg date, culmen length, culmen depth, flipper length, body mass, sex, and carbon and nitrogen isotopes from blood samples. For this project we are not interested in the nesting properties, but rather the physical and chemical penguin properties. Thus, we've disposed data of the individual IDs, nesting stage, clutch completion and egg date. Additionally, samples with missing data were disposed of, decreasing the dataset to a sample size of 330. The categorical values, such as the sex, island and species names, were converted to numerical integers (male = 0, female = 1; Biscoe = 0, Torgersen = 1, Dream = 2; Adelie = 0, Gentoo = 1, Chinstrap = 2). 
Figs. 1,2 and 3 show pie charts of the distribution based on the penguin species, geographic region (islands) and sex. Pairwise relationship are also plotted, showing the relationship between the features for each categorical group of species, islands and sex in Figs. 4,5 and 6, respectively.
We note a more defined grouping in the case of species (Fig. 4), especially with physical attributes such as the culmen length and depth, as well as the chemical attribute for carbon isotopes. On the other hand, this clear grouping can't be seen for the islands feature, although penguins originating from Torgersen seem to have unique features in some of the cases (Fig. 5). Lastly, the sex feature also doesn't visually appear to be organized into distinguishable groups, although there seems to be a more organized grouping for the culmen length and depth (Fig. 6). These figures give us a sense of how well the model will perform based on the chosen output. Given these figures, visual conclusions would imply that a supervised model with an output category like species would yield better results.

![](assets/IMG/pairplot-3.png)

*Figure 4: Pairwise relationships between features for the three different penguin species: adelie (0), gentoo (1) and chinstrap (2).*

![](assets/IMG/pairplot_island.png)

*Figure 5: Pairwise relationships between features for the three different penguin species: Biscoe (0), Torgersen (1) and Dream (2).*

![](assets/IMG/pairplot_sex.png)

*Figure 6: Pairwise relationships between features for the two penguin sexes: male (0) and female (1).*

## Modelling

Here are some more details about the machine learning approach, and why this was deemed appropriate for the dataset. 

The model might involve optimizing some quantity. You can include snippets of code if it is helpful to explain things.

```python
from sklearn.ensemble import ExtraTreesClassifier
from sklearn.datasets import make_classification
X, y = make_classification(n_features=4, random_state=0)
clf = ExtraTreesClassifier(n_estimators=100, random_state=0)
clf.fit(X, y)
clf.predict([[0, 0, 0, 0]])
```

This is how the method was developed.

## Results

Figure X shows... [description of Figure X].

## Discussion

From Figure X, one can see that... [interpretation of Figure X].

## Conclusion

Here is a brief summary. From this work, the following conclusions can be made:
* first conclusion
* second conclusion

Here is how this work could be developed further in a future project.

## References
[1] DALL-E 3

[back](./)

