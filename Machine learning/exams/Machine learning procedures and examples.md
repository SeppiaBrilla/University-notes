
# [[Classification]]

## [[Decision tree]] 
``` python
from sklearn.tree import DecisionTreeClassifier
```
The only parameter is 'max_depth' and it can vary from 1 to decision_tree.tree_.max_depth with decision_tree the tree obtained with unlimited max depth.

## [[K nearest classifier]]
```python 
from sklearn.neighbors import KNeighborsClassifier
```
The only parameter is n_neighbors and a good start for the guess is the sqrt of the number of datapoints.

## [[Adaboost]]
```python 
from sklearn.ensemble import AdaBoostClassifier

params = {'n_estimators':[20,30,40,50], 'learning_rate':[0.5,0.75,1,1.25,1.5]}
```

# [[Clustering]]

## [[K-means]]
```python
from sklearn.cluster import KMeans
```
It only needs the number of clusters to search. The inertia can be obtained with k_means.inertia_. 

## [[Density based clustering|DBSCAN]]
```python
from sklearn.cluster import DBSCAN

dbscan = DBSCAN()
y_pred = dbscan.fit_predict(X)

n_clusters = np.unique(y_pred[y_pred != -1])
if n_clusters > 1:
	silhouette_value = silhouette_score(X, y_pred)
```
The parameters are eps and min_sample. min_sample can be 2 * dimensions of the dataset. eps can be chosen as the elbow of the k-distance with k = min_sample 

## Gaussian mixture ([[Model based clustering]])
```python
from sklearn.mixture import GaussianMixture
params = [{'n_components':range(2,4), 'max_iter':range(100,500,10), 'n_init':range(1,4), 'init_params':['kmeans', 'k-means++', 'random']}]
```

## Agglomerative ([[Hierarchical clustering]])
```python
from sklearn.cluster import AgglomerativeClustering
params = [{'n_clusters':range(2,4), 'metric':['euclidean', 'l1', 'l2', 'manhattan', 'cosine'], 'linkage':['ward', 'complete', 'average', 'single']}]
if parameter['linkage'] == 'ward' and parameter['metric'] != 'euclidean':
	continue
```

### K distance
```python
def k_distance(X, k):

	k_distances = []
	for i in range(0, X.shape[0]):
		k_point_distances = []
		for j in range(0, X.shape[0]):
			if i!=j:
				dist = np.sqrt(sum((X[i,:]-X[j,:])**2))
				k_point_distances.append(dist)
		k_point_distances.sort()
		k_distances.append(k_point_distances[k-1])
		
	k_distances.sort(reverse=True)
	return k_distances
```

# Extra
```python
from sklearn.model_selection import train_test_split
from sklearn.model_selection import cross_val_score
from sklearn.model_selection import ParameterGrid
from mlxtend.plotting import plot_confusion_matrix
from sklearn.metrics import confusion_matrix
from sklearn.model_selection import cross_val_score
from sklearn.metrics import accuracy_score
from sklearn.preprocessing import OrdinalEncoder
from sklearn.metrics.cluster import silhouette_score

import warnings
warnings.filterwarnings('ignore')

try:
	import google.colab.files
	IN_COLAB = True
except:
	IN_COLAB = False
	# from google.colab import files
if IN_COLAB:
	uploaded = files.upload()

data = data[~data.isnull().any(axis=1)] # remove rows with null values 
data = data.dropna(how='any')
data.isnull().sum() > 0 # check column with null values

cross_val_score(model, X_train, y_train, scoring='accuracy')

plot_confusion_matrix(confusion_matrix_test, show_normed=True);

def two_plots(x, y1, y2, xlabel, y1label, y2label):

	fig, ax1 = plt.subplots()
	
	color = 'tab:red'
	ax1.set_xlabel(xlabel)
	ax1.set_ylabel(y1label, color=color)
	ax1.plot(x, y1, color=color)
	ax1.tick_params(axis='y', labelcolor=color)
	
	ax2 = ax1.twinx() # instantiate a second axes that shares the same x-axis
	color = 'tab:blue'
	ax2.set_ylabel(y2label, color=color) # we already handled the x-label with ax1
	ax2.plot(x, y2, color=color)
	ax2.tick_params(axis='y', labelcolor=color)
	ax2.set_ylim(0,1) # the axis for silhouette is [0,1]
	fig.tight_layout() # otherwise the right y-label is slightly clipped
	
	plt.show()


def transform(y_true, y_pred):
	y_mapped = y_pred.copy()
	for lab in np.unique(y_pred):
		if y_true.str.contains(lab).any():
			true_l, count = np.unique(y_true[y_pred==lab], return_counts=True)
			y_mapped[y_pred==lab] = true_l[np.argmax(count)]
		else:
			y_mapped[y_pred==lab] = lab
	return y_mapped

```

### General training process
```python 
paramters_range = [{'p1':value_range_p1, '...', 'pn':value_range_pn}]
parameters = list(ParameterGrid(paramters_range))

scores = []

for i in range(len(parameters)):
	model = Model(**(parameters[i]))
	model.fit(x_train, y_train) # y_train only if needed
	y_pred = model.predict(x_test)
	score = compute_Score_with_function(y_test, y_pred)
	
	scores.append(score)

best_parameters = parameters[np.argmax(scores)]
print(best_parameters)
```