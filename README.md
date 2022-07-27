# Face-Recogniton-With-Siamese-Model



### Model Baseline
a

A Siamese network is a class of neural networks that contains one or more identical networks. We feed a pair of inputs to these networks. Each network computes the features of one input. And, then the similarity of features is computed using their difference or the dot product. For same class input pairs, target output is 1 and for different classes input pairs, the output is 0.

Remember, both networks have same the parameters and weights. If not, then they are not Siamese.

By doing this, we have converted the classification problem to a similarity problem. We are training the network to minimize the distance between samples of the same class and increasing the inter-class distance. There are multiple kinds of similarity functions through which the Siamese network can be trained like Contrastive loss, triplet loss, and circle loss.

1. Contrastive loss: In Contrastive loss, pairs of images are taken. For same class pairs, distance is less between them. For different pairs, distance is more. Although binary cross-entropy seems like a perfect loss function for our problem, the contrastive loss does a better job differentiating between image pairs. Contrastive loss, L = Y * D^2 + (1-Y) * max(margin — D, 0)^2
D is the distance between image features. ‘margin’ is a parameter that helps us pushing different classes apart.

<img src= images/Contrastive_loss.png  width = "1000" height = "500">

2. Triplet loss: Triplet loss was introduced by Google in 2015 for face recognition. Here, the model takes three inputs- anchor, positive, and negative. The anchor is a reference input. Positive input belongs to the same class as anchor input. Negative input belongs to a random class other than the anchor class.

<img src= images/triplet_loss.png  width = "1000" height = "500">

The idea behind the Triplet Loss function is that we minimize the distance between the anchor and the positive sample and simultaneously also maximize the distance between the anchor and the negative sample.

Let’s take a look at the mathematical formula of triplet loss.

Here d denotes a distance metric. The distance between anchor and positive should be more than negative and anchor. So, d(a,p) — d(a,n) < 0. To keep it positive, we can modify it like this: Loss L= max(d(a,n) — d(a,p), 0).

To further increase the separation between positive and negative, a parameter ‘margin’ is introduced.

Now, L = max(d(a,n) — d(a,p) + margin, 0)


### Basic structure of a Siamese model
<img src= images/Siamese.png  width = "1000" height = "500">

