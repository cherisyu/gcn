# Graph Convolutional Network  
## Basic Introduction  
An much simpler and easy understand graph convolutional network.  

[original gcn code can be found here](https://github.com/tkipf/gcn)  
[A pretty nice gcn blog can be found here](https://tkipf.github.io/graph-convolutional-networks/)  

This implementation of gcn is easier to understand, which will be more friendly to newcomer.  

## Usage:  
**Input:**  
an edgelist and a label file are must. If feature file is available, gcn will use it for learning.  
If we don't have fearture matrix, the fearure matrix will be replaced by an identity matrix, as we don't have any node features. Besides, we also need to provied the total label numbers for node classification.  
**Parameters:**  
--edgelist: edgelist file, looks like node1 node2 <weight_float, optional>;  
--weighted: treat the graph as weighted; this is an action;  
--directed: treat the graph as directed; this is an action;  
--labels: node labels, looks like node_id label_id;  
--features: node features, looks like node feature_1 feature_2 ... feature_n;  
--label_nums: number of labels. for Wiki dataset, 17 labels; for cora dataset, 7 labels;  
--lr: learning rate, default is 0.01;  
--epochs: training epochs, default is 200;  
--act: activation function, default is relu;  
--clf-retio: the ratio of training data for node classification; the default is 0.5;   
**Environment:** python 3.6, tensorflow 1.11.0  
**DataSet:**  
[datasets are from here](https://github.com/thunlp/OpenNE)  
Wiki : 2405 nodes, 17981 edges, 17 labels, directed, no features;  
Cora : 2708 nodes, 5429 edges, 7 labels, directed, features available;  
**To run the code on Wiki dataset(if you want to treat it as undirected graph):**  
'''
python main.py --edgelist data/wiki/Wiki.edgelist --labels data/wiki/Wiki.labels --label_nums 17 --lr 0.001 --epochs 800  
'''  
**To run the code on Cora dataset(if you want to treat it as directed graph):**  
'''
python main.py --edgelist data/cora/cora.edgelist --labels data/cora/cora.labels --label_nums 7 --features data/cora/cora.features --epochs 500 --directed   
'''  
## Classification accuracy(50% training data):
Wiki: around 0.68-0.71;  
Cora: around 0.77-0.81(without node features), around 0.79-0.84(with node features);  
Note: for both datasets, only training 800 epochs several time, thus the accuracy is not stable.    


