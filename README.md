# Link prediction on the DBpedia graph of musical artists using GraphSAGE

In this work I present a GraphSAGE model for link prediction in the DBpedia graph of musical artists.  The findings are a proof that GraphSAGE excels in the link prediction task, even when given data that is poorly structured and needs a lot of cleaning. It compares the results given the whole musical artist graph and a subset of the graph and concludes that the size of the dataset doesn’t make a difference. Also, this work could serve as a basis for further research in the field of recommendation systems using a link prediction approach. 

## Data retrieval and cleaning

The dataset for this work consists of a graph of artists that share a connection via the dbo:associatedMusicalArtist property and a table of genres associated to these artists as node features in the graph. It was queried from the DBpedia SPARQL endpoint directly from the code (data_mining notebook). The data was very noisy and required manual cleaning, as well as some transformations (like one-hot encoding genres and droping rows from both tables).

## Models and Results

Two link prediction models were built: One on the whole graph and node features and another on a reduced subset of these datasets. The models were built using the stellargraph library for Python (which uses Tensorflow and Keras) and a model calibration was done afterwards. The results for both models are the following:
|           | Model on whole graph | Model on reduced graph |
|-----------|----------------------|------------------------|
| Accuracy  | 0.8465               | 0.8310                 |
| Precision | 0.8454               | 0.8103                 |
| Recall    | 0.8481               | 0.8644                 |
| F1-score  | 0.8468               | 0.8365                 |
