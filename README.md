# Speaker Verification using Siamese Networks

This project presents an innovative approach to speaker verification utilizing Siamese Networks, a powerful architecture within the realm of deep learning. The system is designed to determine whether two given speech utterances originate from the same speaker or not, a critical task with applications spanning security systems, personalization features, and beyond.

## Problem Overview

The dataset comprises two components: a training set (`trs.pkl`) and a test set (`tes.pkl`). Each dataset consists of matrices representing speech signals, with rows corresponding to individual utterances. The training set encompasses utterances from 50 speakers, each contributing 10 samples, while the test set features 20 speakers, also with 10 utterances each.


### Siamese Network

The cornerstone of this project lies in the Siamese network architecture. Siamese networks consist of twin neural networks with shared weights. These networks receive pairs of inputs and learn to produce embeddings, which capture the essential characteristics of the input data. By comparing the embeddings of two input samples, the network determines their similarity. Siamese networks excel at tasks involving similarity assessment. Each input sample is processed by an identical neural network (the twin network), generating an embedding. These embeddings are then compared, typically using metrics like Euclidean distance or cosine similarity, to measure the similarity between the input samples. Siamese networks are particularly effective in scenarios where labeled training data is scarce, as they can learn to distinguish between classes by comparing individual samples.


#### Network Architecture

The specific architecture of the Siamese network can be flexible. For this project, consider using a recurrent neural network (RNN) such as Gated Recurrent Unit (GRU) to process the spectrograms. The network should output fixed-length feature vectors for the input pairs, which are then passed through a sigmoid function for binary classification.

## Requirements

Ensure you have the following dependencies installed:

- Python 3.x
- NumPy
- SciPy
- Librosa
- TensorFlow


## Approach

### 1) Data Data Preparation:
-   Randomly sampled positive and negative pairs of utterances.
-   Positive pairs: Pairs of utterances from the same speaker.
-   Negative pairs: Pairs of utterances from different speakers.
-   Formed minibatches with balanced positive and negative pairs.

### 2) Feature Extraction:
-   Applied Short-Time Fourier Transform (STFT) to the signals to obtain spectrograms.
-   Each spectrogram is of size 513xT, representing frequency bins over time.


### 3) Siamese Network
-   Designed a Siamese network architecture.
-   Each branch of the Siamese network processes one spectrogram.
-   Extracted fixed-length feature vectors for each spectrogram.
-   Combined the feature vectors and compute the inner product.
-   Passed the result through a sigmoid function for logistic regression

### 4) Training:

-   Trained the Siamese network on minibatches of positive and negative pairs.
-   Used the inner product of feature vectors as input for binary classification.


### Results:
-   Achieved a verification accuracy of approximately 70%.
-   Utilized a reasonable network architecture of GRUs.
-   Convergence achieved within a reasonable training time of within one hour

## Getting Started

To get started with this project, follow these steps:

1. Clone the repository: `git clone [repository_url]`
2. Install dependencies: `pip install -r requirements.txt`
3. Run the provided scripts or notebooks to train the Siamese Network.
4. Explore the results and experiment with different parameters to deepen your understanding.

## Results

Upon training the Siamese network with the provided dataset, a verification accuracy of approximately 70% was achieved on the test examples.

## Acknowledgement

This project would like to thank the developers of TensorFlow, and librosa for providing the tools and libraries for Speech Processing and Neural Networks that made this project possible

## Licenses

This project is licensed under the [License Name] - see the [LICENSE.md](LICENSE.md) file for details.
