# TSNE visualization of the embeddings extracted from mfvae

Please click [here](https://jerrypeng21cuhk.github.io/2dVisualEmbedding/) to see the visualization.

mfvae is an unsupervised trained model that attempts to decompose a speech signal into two independent representations: a sequence of discrete tokens that represents linguistic information and an utterance embedding that captures paralinguistic information, e.g., the speaker identity.

This visualization is to give a qualitative evaluation of the model.
60 speakers are randomly selected from the voxceleb1_train.
On the left panel, there are three configurations: **speaker label**, **GMM**, **AHC** which represent the coloring method to these embeddings.

**speaker label** means use the speaker label to grant the same color for the embedddings from the same speaker.
GMM and AHC means Gaussian Mixture Model and Agglomerative Hierarchical clustering methods which assign embeddings pseudo labels and color the embeddings according to these pseudo labels, similar as **speaker label**.


## Some observations:
1. There exists a boundary that separate these embeddings into two clusters, the above and the below representing female utterances and male utterances.
2. As each speaker is represented as a cluster of embeddings, compared the male with female, male speakers are more seperable with each other.

## Tips:
1. Press *Ctrl* and hover your mouse over the points, the detail information of each point will appear.
2. You can add a directory named as **audio** that stores the training audios. Then by click each single node, you are able to listen the utterances.
The training audios should be stored in this structure (almost the same as the voxceleb1 dataset folder structure): audio/train/wav/id1001/1zclwhmde04/0001.wav

A simple cosine scoring on the embeddings extracted from mfvae on VoxCeleb1_test is: EER 14.4%. With PLDA, the EER is reduced to around 7%, which verifies the embeddings captures speaker information.
It should be noted that the embeddings may also cpature other information that is stationary within an utterance.
You may regard the **embedder** part of mfvae as an neural network version i-vector method.
