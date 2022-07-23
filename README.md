*HeartSpot*: Privatized and Explainable Data Compression for Cardiomegaly Detection
===

#### NOTE:  The paper was accepted but not yet published.  I will remove the TODO statements after the paper is published.

![figure 1 of paper](./heartspot_fig1.png)
![figure 2 of paper](./arch_diagram.png)

This repository contains code for the conference paper.

- Citation:

```
TODO
```

- Bibtex:

```
TODO

```


- Paper on ArXiv:  **TODO: add url after conference**
- Paper on IEEE, as published via conference BHI-BHN 2022:  **TODO:  add URL after conference**


Reproducibility
===

#### Git clone this repository, cd into it, and create a `./data` dir.

```

$ git clone https://github.com/adgaudio/HeartSpot.git
$ cd HeartSpot
$ mkdir data
```

#### Download the CheXpert-v1.0-small dataset into `./data/`

CheXpert dataset download link:  https://stanfordmlgroup.github.io/competitions/chexpert/

```
# after downloading, ensure your directory structure matches this
$ find ./data/CheXpert-v1.0-small/ -maxdepth 1
    data/CheXpert-v1.0-small/
    data/CheXpert-v1.0-small/train.csv
    data/CheXpert-v1.0-small/train
    data/CheXpert-v1.0-small/valid
    data/CheXpert-v1.0-small/valid.csv

# the dataset is about 12gb
$ du -sm data/CheXpert-v1.0-small/
    12366   data/CheXpert-v1.0-small/
```

#### Set up your python environment.

I used anaconda with python 3.9.7 and these packages (and several others not mentioned).

```
torchvision==0.10.1
pytorch==1.9.1
captum==0.4.0
scipy
numpy
matplotlib
IPython
opencv
seaborn
pandas
gzip
lzma

pampy==0.3.0
simple-parsing==0.0.17
efficientnet-pytorch

pip install --no-deps simplepytorch==b76cfc51d015deb043cc071dc6c9c28aefe770e9

# hopefully no others are missing.  raise an issue so I can update the readme if
there is a missing requirement.
```

#### Reproduce the HeartSpot experiments:

You should review the code yourself before running it.  The script expects you
have redis-server installed and running and will try to parallelize jobs across
available GPUs.  I suggest to read the bottom of the file first.

I used two GPUs with 11gb of GPU RAM, a CPU with 24 cores and 128GB RAM.
You may need to tweak num_workers and batch_size accordingly.

```
$ ./bin/experiments_heartspot.sh
```

#### Reproduce the plots:

```
$ ls bin/plot*hline*
 bin/plot_hline_acc_vs_time.py      bin/plot_hline_getsaliency2.py
 bin/plot_hline_archdiagramfigs.py  bin/plot_hline_getsaliency.py
```
