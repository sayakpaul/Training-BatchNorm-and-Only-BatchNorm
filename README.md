# Training-BatchNorm-and-Only-BatchNorm
Experiments with the ideas presented in [Training BatchNorm and Only BatchNorm: On the c of Random Features in CNNs](https://arxiv.org/abs/2003.00152) by Frankle et al. In this paper, Frankle et al. explore the expressiveness of the random features in CNNs by starting with the following experimental setup:
- They first set all the layers of a CNN to `trainable=False`. 
- Before they kickstart model training, they also set the Batch Norm layers to be trainable. 

This simple experimental setup led to some pretty amazing discoveries on the expressive power of the randomly initialized layers in a CNN. So, the authors further explore the question - *what if we only train the Batch Norm layers and lead this setup to a potential optimum?* Their findings were pretty intriguing.

## Dataset used
CIFAR10

## Architecture used
ResNet20 (Thanks to the [Keras Idiomatic Programmer](https://github.com/GoogleCloudPlatform/keras-idiomatic-programmer) repo)

## About the files
- `CIFAR10_Subset.ipynb`: Runs experiments on a GPU with a subset of the CIFAR10 dataset. 
- `CIFAR10_Full.ipynb`: Runs experiments on a GPU with the full CIFAR10 dataset.
- `CIFAR10_Full_TPU.ipynb`: Runs experiments on a TPU with the full CIFAR10 dataset.
- `CIFAR10_Full_TPU_Different_LR_Schedules.ipynb`: Runs experiments on a TPU with the full CIFAR10 dataset but with different learning rate schedules.
- `All_Layers_Frozen.ipynb`: As the name suggests this notebook shows what happens when all the layers of a CNN is made _non-trainable_.
- `Varying_Batch_Sizes.ipynb`: Runs experiments with varying batch sizes (only batch norm layer as trainable).
- `Visualization.ipynb`: Visualizes the learned convolution filters of the networks. 
- `Visualization_II.ipynb`: Almost same as `Visualization.ipynb` with a bit different visualization plots. 

## Some interesting findings (of course credits to the authors)
Below is the output of the first trained convolution layer (**all the layers were trained from scratch in this case**)
![](https://i.ibb.co/ZTdY4pB/download.png)
Below is the output of the first trained convolution layer (*this time only the Batch Norm layers were trained*)
![](https://i.ibb.co/drPbsnP/download-1.png)

More results can be found here: https://app.wandb.ai/sayakpaul/training-bn-only. 

## Important note
I trained both the variants of the networks for 75 epochs. Naturally, the one that contains only the BN layers as trainable ones would take longer to converge because of the number of parameters. But that can be used as a proxy to alleviate the problems of huge model size.

## Acknowledgements
Although the notebooks are available as Colab-ready I trained all of them on a pre-configured AI Platform Notebook to make the experiments more reproducible. Thanks to the **ML-GDE program** program for the GCP Credits. 
