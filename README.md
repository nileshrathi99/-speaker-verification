# Speaker Verification System

## Problem Description

This project involves building a speaker verification system using Siamese networks. The task is to predict whether two given utterances belong to the same speaker (positive class) or different speakers (negative class).

## Dataset

- **Training Data (trs.pkl):** Contains a 500×16,180 matrix of speech signals, where each row represents a speech signal with 16,180 samples. The matrix is ordered by speakers, with each of the 50 speakers having 10 utterances.

- **Test Data (tes.pkl):** Holds a 200×22,631 matrix with a similar structure as the training set, featuring 20 speakers with 10 utterances each.

## Implementation Steps

1. **Positive and Negative Pair Sampling:**
   - Randomly sample L pairs of utterances from the ten utterances of the first speaker. There are theoretically 45 pairs to choose from.
   - Construct L negative pairs by randomly sampling L utterances from the 49 other training speakers and pairing them with L utterances from the first speaker.

2. **Feedforward and Parameter Update:**
   - Implement feedforward using the Siamese network architecture.
   - Update parameters.

3. **Minibatch Construction and Training:**
   - Form 50 minibatches with a balanced number of positive and negative pairs from different training speakers.
   - Train the Siamese network to predict 1 for positive pairs and 0 for negative pairs.

4. **Siamese Network Design:**
   - Use STFT on the signals for feature extraction.
   - Design a Siamese network that takes two spectrograms (size 513 × T) as input and predicts a fixed-length feature vector for each.

5. **Test-time Speaker Verification:**
   - Construct similar batches from the test set.
   - Evaluate the verification accuracy of the trained network on the test examples.
