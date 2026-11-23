# Lab 02: Neural networks on MNIST

Build, train and tune dense (fully connected) neural networks in **TensorFlow / Keras 3** to classify handwritten digits from the MNIST dataset.

## Data

MNIST: 70,000 grayscale images of handwritten digits, 28×28 pixels, 10 classes (0–9). Downloaded from OpenML (dataset 554) on first run, then cached, so there is no `data/` folder.

Official split: first 60,000 rows for training, last 10,000 for testing (`shuffle=False`).

## Method

- Pixels scaled from [0, 255] to [0, 1]; labels one-hot encoded.
- Model: `Flatten` → hidden `Dense` (ReLU) layers, each optionally followed by `Dropout` → `Dense(10, softmax)`. Loss: categorical cross-entropy, optimizer: Adam. Seed fixed (`SEED = 0`).
- **Baseline (Ex. 4)**: 1 hidden layer of 32 units, dropout 0.3, learning rate 0.003, 50 epochs, batch size 4000, 20% of the training data held out for validation.
- **Tuning (Ex. 5)**: manual search over 8 configurations varying the number of hidden layers (1–3), nodes per layer (128–1024) and the number of dropout layers / dropout rate (0–0.4). Batch size 256, learning rate 0.001, early stopping on validation accuracy (patience 5, best weights restored).
- Configurations are selected on the validation set only. The test set is used once, on the selected model.

## Results

| Model | Validation accuracy | Test accuracy |
|-------|---------------------|---------------|
| Baseline, 32 units | 0.953 | 0.953 |
| Tuned, 512-256-128 with dropout 0.2 | 0.983 | **0.982** |

The tuned model clears the 96% target and misclassifies 184 of the 10,000 test images.

Validation accuracy of the tuned configurations:

| Configuration | Val. accuracy |
|---------------|---------------|
| 512-256-128, dropout 0.2 | 0.9825 |
| 1×512, dropout 0.2 | 0.9823 |
| 2×256, dropout 0.2 (one layer) | 0.9823 |
| 1024-512, dropout 0.4 | 0.9818 |
| 512-256, dropout 0.3 | 0.9814 |
| 512-256-128, dropout 0.3 | 0.9796 |
| 2×256, dropout 0.2 (both layers) | 0.9790 |
| 1×128, no dropout | 0.9772 |

Wider layers and a smaller batch size drive most of the gain over the baseline, while depth barely matters. Without dropout, the model reaches 100% training accuracy and has the lowest validation accuracy. The top configurations differ by about 0.1–0.4%, which is close to run-to-run noise, so the ranking should not be over-read. Going much beyond ~98% would need a CNN.

## Run

See the [root README](../README.md) for setup, then open `lab2.ipynb` and run all cells. The first run needs internet access to download MNIST.
