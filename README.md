# Learning Type-Aware Embeddings for Fashion Compatibility

fashion-compatibility contains a [PyTorch](http://pytorch.org/) implementation for our [paper](https://arxiv.org/pdf/1803.09196.pdf).  If you find this code or our dataset useful in your research, please consider citing:

    @inproceedings{VasilevaECCV18FasionCompatibility,
    Author = {Mariya I. Vasileva and Bryan A. Plummer and Krishna Dusad and Shreya Rajpal and Ranjitha Kumar and David Forsyth},
    Title = {Learning Type-Aware Embeddings for Fashion Compatibility},
    booktitle = {ECCV},
    Year = {2018}
    }

This code was tested on an Ubuntu 16.04 system using Pytorch version 0.1.12.  It is based on the [official implementation](https://github.com/andreasveit/conditional-similarity-networks) of the [Conditional Similarity Networks paper](https://arxiv.org/abs/1603.07810).


## Usage
You can download the Polyvore Outfits dataset including the splits and questions for the compatibility and fill-in-the-blank tasks from [here](). After unpacking the dataset make any necessary updates to the data root directory in polyvore_outfits.py. 

Afterwards, you can train the model using `python main.py`.  You can see a listing and description of many tuneable parameters with:

```sh
    python main.py --help
```

For example, to learn masks used for the projections for each type specific embeddings, rather than the default which creates fixed masks, you would use:

```sh
    python main.py --name {your experiment name} --learned
```

By default the code outputs the results on the test set after training. However, if you wanted to re-run the test for many settings you have to use the same flags during testing as you had during training.  For example, if you trained with the `--use_fc` to train fully connected type-specific embeddings rather than a mask, at test time you would use:

```sh
   python main.py --test --use_fc --resume runs/{your experiment name}/model_best.pth.tar
```

