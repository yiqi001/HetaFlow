# HetaFlow



## Requriment
To run the code of this repository, the following requriments are needed.
- python 3
-  Intall this lib first: [dgl](https://github.com/dmlc/dgl)

## Simple Run
Dowload the repository, intall the requriments. Excute the following in a CMD or shell or terminal:
`python train_HetaFlow_attention_along_path8_DBLP.py --dataset=DBLP`

This is the output:
```
C:\Users\some\path> python train_HetaFlow_attention_along_path8_DBLP.py --dataset=DBLP
Namespace(alpha=0.2, dataset='DBLP', dropout=0.6, epochs=200, fastmode=False, gpu=-1, in_drop=0.6, learning_rate=0.005, negative_slope=0.2, no_cuda=True, num_heads=1, num_hidden=7, num_layers=1, num_out_heads=1, residual=False, seed=88, syn_gnp_n=1000, syn_gnp_p=0.0, syn_nclasses=10, syn_nfeats=500, syn_seed=42, syn_test_ratio=0.5, syn_train_ratio=0.1, syn_type='gnp', syn_val_ratio=0.2, weight_decay=0.0005)
loading dataset  DBLP


attention layers in_features out_features 7 7
train_steps 140
val_steps 300
test_steps 300
Epoch [1/200], Step [140/140], Loss: 0.0000 epoch_loss 50.859074115753174  Accuracy on val data: 85.34 %
Epoch [2/200], Step [140/140], Loss: 0.0000 epoch_loss 48.627846479415894  Accuracy on val data: 88.65 %
Epoch [3/200], Step [140/140], Loss: 0.0000 epoch_loss 46.63915514945984  Accuracy on val data: 90.07 %
...
Epoch [62/200], Step [140/140], Loss: 0.0000 epoch_loss 28.78111696243286  Accuracy on val data: 94.0 %
Epoch [63/200], Step [140/140], Loss: 0.0000 epoch_loss 28.745331287384033  Accuracy on val data: 94.1 %
Accuracy on test data: 93.6 %
```

## Detail Run
- Step1
Decompse a graph data (DBLP) in to flows.
`python train_decompose_graph_DBLP.py --dataset=DBLP`
It will produce a file to store the flows. It is named **decomposed_paths_central_rectangle_DBLP**.

- Step2
Produce the node vectors using a two layer attention model(GAT).
`python train_gen_vec_DBLP.py --dataset=DBLP`
It will produce a file to store node vector. It is named **logits_of_DBLP**

- Step3
Train a HetaFlow model who's attention is along flows or paths and test its accuracy.
`python train_HetaFlow_attention_along_path8_DBLP.py --dataset=DBLP`

