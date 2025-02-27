# bis-assignment-20020228

Clustering Evaluation and Visualization

Overview

This project applies clustering techniques (K-Means and DBSCAN) to segment customer data based on Annual Income and Spending Score. The clusters are evaluated using the Silhouette Score, and results are visualized using Matplotlib and Bokeh.

Installation

To run the project, install the required dependencies:

pip install numpy pandas scikit-learn matplotlib bokeh

Clustering Methods Used

K-Means Clustering

Used to segment customers into different groups.

The optimal number of clusters is determined using the Elbow Method and Silhouette Score.

DBSCAN (Density-Based Spatial Clustering)

An alternative to K-Means for identifying noise and dense clusters.

Works well for irregularly shaped clusters.

Evaluating Clusters

Silhouette Score

The Silhouette Score measures how well each data point fits within its assigned cluster.

from sklearn.metrics import silhouette_score

final_score = silhouette_score(df_scaled, final_labels)
print(f'Silhouette Score for final clusters: {final_score:.4f}')

Score near 1: Clusters are well-separated.

Score near 0: Overlapping clusters (weak separation).

Score near -1: Misclassified points.

Improving a Weak Silhouette Score:

Try different numbers of clusters for K-Means.

Use PCA or t-SNE for dimensionality reduction before clustering.

Experiment with DBSCAN for non-linear clusters.

Visualizing Results

Matplotlib Scatter Plot

import matplotlib.pyplot as plt
plt.scatter(df['Annual Income'], df['Spending Score'], c=final_labels, cmap='viridis')
plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.title('Customer Segments: Annual Income vs. Spending Score')
plt.show()

Bokeh Interactive Plot

from bokeh.plotting import figure, show
from bokeh.io import output_notebook

output_notebook()

p = figure(title="Bokeh: Customer Segments",
           x_axis_label='Annual Income (k$)',
           y_axis_label='Spending Score (1-100)',
           width=700, height=500)
show(p)

Conclusion

K-Means performed better than DBSCAN in this dataset.

Silhouette Score helped validate cluster quality.

Bokeh enables interactive visualizations to explore customer segments.

Future Improvements

Test Hierarchical Clustering.

Optimize K-Means with different distance metrics.

Implement Feature Engineering to improve clustering results.
