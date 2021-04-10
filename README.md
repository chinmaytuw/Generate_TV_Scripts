# Generate_TV_Scripts


## Intro:
This project generates Seinfeld TV scripts using RNNs.

We have Seinfeld dataset of scripts from 9 seasons. The Neural Network generates a new ,"fake" TV script, based on patterns it recognizes in this training data.

## Choosing the hyperparameters
Choosing the hyperparameters requires not only knowledge, but also luck, intuition, and patience. Especially, patience. One epoch takes more than an hour and it's really hard to observe the training and not to try to improve it at the same time.

Learning rate = 0.001
0.01 is a good starting point. 0.001, 0.0001, and 0.1 are also good values.

I tried 0.01, but the network was not learning, while 0.001 allows the network to improve the loss fast.

Sequence length = 12
I didn't find specific recommendations about sequence length, the common answer is, "it depends."
I noticed that shorter sequence length makes faster iterations with good improvements in the loss.

I started with sequence length = 200 and every epoch was literally talking hours. Decreasing the sequence length was the most impactful decision in this project as it allowed the model to train much faster (<15 minutes per epoch) while almost not affecting the loss.
Setting a low sequence length allowed me to experiment with other parameters.

Batch size = 128
According to the course, recommended starting point is 32. 32 to 256 are potentially good starting values. Larger size may computational boost due to optimized matrix multiplication, but it can stuck in local minimum.

I also tried 64, it was slightly faster and producing slightly better loss.

Embedding dimension = 500
The example architectures use embedding dimension from 100 for text summarization to 1000 for translation.
After experiment with other values (e.g., 200), I chose a value in between: 500 to give the network more capacity to learn.

Long Short-Term Memory (LSTM) or Gated Recurrent Unit (GRU)? LSTM
There is no universal advice on whether to use LSTM or GRU.
I started with LSTM, and also tried GRU. LSTM was producing better results.

Number of RNN layers = 3
General recommendation is to choose two or three layers. I chose three layers to give my network more capacity to learn.

Hidden dimension = 600
The example architectures use size from 200 for text summarization to 1000 for speech recognition for large vocabulary.
I chose 600 because my embedding dimension was 500. Intuitively, the hidden dimension should be greater than the embedding dimension.
I also tried 200 while using 200 for the embedding dimension.

I chose Embedding dimension = 500 and Hidden dimension = 600 because their training loss was slightly better than for lower values while almost not affecting the training time.
