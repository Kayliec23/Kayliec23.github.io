## Exploring Machine Learning Techniques Using the Palmer Penguin Dataset

I applied machine learning techniques to investigate different classification models usingthe Palmer Penguin dataset.

***

## Introduction

In this study we will use the Palmer Penguin dataset [1] from the UCI Machine Learning Repository to evaluate and compare logistic regression model with Multi-Layer Perceptron (MLP) Classifier Neural Network. The purpose of this study is to compare the performance of the two models for binary classification as well as multi-classification. To do this we will examine three sets of outcomes: penguin species, geographical location of the penguins, and penguin sex. The first two outcomes can be classified into three classes, whereas the last into two.

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

To determine the relationships between the independent and dependent variables, we will compare two models: the classic logistic regression model and a Multi-Layer Perceptron (MLP) classifier neural network. 

Logistic regression models are supervised machine learning models that, unlike in linear regression models, are used for categorical data that deals with integer values. The species, sex and island data can be represented as integer values 0,1,2, etc. and therefore as categories . We note that for species and islands, there are three categorical classes, and therefore we used the multinomial fit in the logistic regression model. Unlike linear regression models that fit a slope to this data, logistic regression models are a classification model and use a tanh like function that can better represent the process of categorization into these groups.

The second model is a neural network. The way a neural network works is through nodes of layers, where there always exists an input layer, output layer and hidden layers in between. We call these nodes neurons (the idea of neural networks was inspired by how the brain works), where the neurons are connected to one another through weights and thresholds. In order for communication to take place, the threshold needs to be met. Thus, we will need to construct a neural network structure. The network chosen consists of three layers: the input layer, the hidden layer and the output layer. The input layer consists of the independent variables (culmen length, culmen depth, flipper length, body mass, sex, island, carbon isotope and nitrogen isotope). The hidden layer consists of three neurons and the output layer will have three in the cases of species and island, and 2 in the case of sex. The number of layers was chosen for simplicity and the number of neurons in each hidden layer were chosen based on the rules of thumb taught in class. Mainly, I chose for the number of hidden neurons to be equal to 2/3 of the input and output neurons. For consistency, I approximated this as 8. It should be noted that I chose one hidden layer, but more variants should be examined with more hidden layers. 

In essence, each node is it's own logistic regression model, that receives it's own input data, weights, biases, etc. As part of the model training process, it will evaluate the accuracy of the model using an appropriate form of the cost function. The goal is to minimize this cost function in accordance to adjustments being made to the weights and biases which is doe in a process called gradient descent. To implement this in our neural network, we use the Multi-Layer Percepton (MLP) Classifier. The MLP Classifier is a supervised learning algorithm that trains using gradient descent in the form of a stochastic gradient-based optimizer, where the gradients are calculated using backpropagation. Backpropagation allows us to move from output to input ("backwards") so that we can calculate and attribute the error associated with each neuron, and thereby allowing us to more effectively adjust and fit the parameters of the model. Additionally, the activation function used in the hidden layer is the rectified linear unit function.

Lastly, the dataset was split into training and testing data. 20\% of the data was reserved for checking the accuracy of the trained model, while the data was scaled independently when used as model input. 

## Results

Here we evaluated the models' accuracy for species, islands and sex. Additionally, in order to evaluate the performance of the classification, we used a confusion matrix, which is suited for classification models using supervised learning frameworks. These results will help us understand where the model has gone wrong, and allows for more transparency in case the model is falsely predicting the correct classification.

### Species

We examined the logistic regression model's ability to accurately predict the probability of the three different penguin species -- Adelie, Gentoo and Chinstrap -- based on the independent variables. We found that the accuracy score was 100\%. We've also examined the confusion matrix, plotted in Fig. 7. The results indicate that all penguin species are identified correctly.

![](assets/IMG/confusionMatrix.png)

*Figure 7: Confusion matrix evaluating logistic regression model predicting species.*

The neural network performs well for the species output, with an accuracy of $98.48\%$, with only one Adelie pengui mislabeled as a Chinstrap penguin. Results of the confusion matrix can be seen in Fig. 8.

![](assets/IMG/confusionMatrix_MPLC_sex-4.png)

*Figure 8: Confusion matrix evaluating MLP Classier NN predicting species.*

### Islands
Interestingly, when we move to classifying by the geographical setting, i.e., the islands, the model's accuracy significantly reduces. In the logistic regression model,the value reduces to $69.70\%$. To avoid reptition, we will not plot the confusion matrix again, but note that there are a fair amount of instances that are mislabeled, where the most amount of errors that arise are due to Dream being predicted as Torgersen. Similar to the logistic regression model, the neural network does a somewhat decent job at categorizing islands, but is not excellent, with an accuracy of $68.18\%$. Most of the errors come from mislabeling 9 cases Torgersen as Dream and another 8 of Biscoe as Dream.

### Sex

Lastly we evaluated the model when classifying based on the penguin's sex: male or female. The accuracy of the logsitic regression model is 78.79\%. The model has five cases where females are mislabeled as male, and nine cases where males are mislabeled as females. The MLP Classifer NN performs better, with an accuracy of 87.88\% and five males mislabeled as male and 3 females mislabeled as male. 

## Discussion

On the whole, the logistic regression model performed slightly better than the multi-layer perceptron (MLP) classifier neural network (NN). We mainly see a difference for the classifying case of penguin sex. Both models scored relatively low accuracy for the island and penguin sex category, although their confusion matrices weren't behviorally similar. Most of the errors in the MLP classifier NN were because the model falsely labeled instances as Dream Island. However, for the linear regression model the instances mislabeled were randomly scattered in the confusion matrix. This leads me to believe that the MLP classifier NN perhaps could be fixed with some finer tuning, since the error seems to have a pattern where most mislabeled instances belong to Dream Island. It's worth keeping in mind that when we look at the pair relationship plots for islands, the relationship between the features and the penguins' geographic location, visually there appears to be a weaker relationship, and so perhaps it would be worth examining a subset of input features. 

The confusion matrices for the penguin sex category had errors split quite evenly for the MLP classifier NN, but the logistic regression model leaned more heavily towards errors where females were mislabeled as males. Perhaps this is indictive of better tuning needed, however, the MLP Classifer NN does  sigificantly better job tha the logistic regression model at predict penguin sex and perhaps should be the prefered model for this. Noticeably, this is the category with only two classes, and raises the question whether perhaps the MLP Classifier NN performs better for smaller class groups. 

It is worth noting, in both the sex and island categories, but in particular with the penguin sex category, changing the size of the hidden layer affected the results greatly. In another run with a hidden layer = 3, the accuracy dropped to 68.36% , indicating the importance of the hidden layer size. 

On the other hand, the species category scored very high in both models, with the logistic regression model scoring 100% accuracy, and the MLP classifier NN ~98%. While it is interesting that the logistic regression scored so highly and that the MLP classifier NN scored lower, they both still scored very highly, thus we can conclude that both models would be appropriate for categorizing the penguin species.

## Conclusion

In this study we've used the Palmer penguins dataset to evaluate a logistic regression model and a multi-layer perceptron (MLP) classifier neural network (NN). We not only compared the models, but we evaluated how the models perform for different output categories with different class sizes. 

Both models performed very well when classifying for penguin species, but less so for penguin sex and the penguin's geographical locations. We saw that, overall, the MLP Classifer NN performed slightly better than the MLP classifier NN. That being said, future work should experiment the the MLP classifier NN. For instance, we had shown in the one example of penguin sex that changing the hidden layer size dramatically changes the results. This is consistent with results we found in our homework assignments, and perhaps should be tested for the categories that perform less well, like the islands. Other noteworthy changes to explore would be the activation function within the hidden layer, the chosen solver for the weight optimization, or the strength of the L2 regularization term. Additionally, the dataset can be filtered into a smaller subset of independent variables, or examined based on scientific attributes (e.g. "physical" (culmen length, culmen depth, flipper length, body mss) and "chemical" (carbon and nitrogen isotopes) attributes). Filtering the input variables might also affect the model performance.

## References
[1] Horst AM, Hill AP, Gorman KB (2020). palmerpenguins: Palmer Archipelago (Antarctica) penguin data. doi:10.5281/zenodo.3960218, R package version 0.1.0, https://allisonhorst.github.io/palmerpenguins/.

[back](./)

