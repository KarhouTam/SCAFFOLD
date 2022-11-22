# SCAFFOLD: Stochastic Controlled Averaging for Federated Learning [[ArXiv]](https://arxiv.org/abs/1910.06378)

This repo is the PyTorch implementation of SCAFFOLD.

I further implement FedAvg and FedProx for you.🤗

For simulating Non-I.I.D scenario, the dataset can be splitted based on Dirchlet distribution or assign random classes to each client.


## Preprocess dataset
  
MNIST, EMNIST, FashionMNIST, CIFAR10, CIFAR100 are supported.

```python
python ./data/utils/run.py --dataset ${dataset}
```
The way of preprocessing is adjustable. Check `./data/utils/run.py` for more argument details
## Run the experiment

❗ Before run the experiment, please make sure that the dataset is downloaded and preprocessed already.

It’s so simple.🤪

```python
python ./src/server/${algo}.py
```

You can check `./src/config/util.py` for all hyperparameters detail.


## Result

Some stats about convergence speed are shown below.

`--dataset`: `emnist`. Splitted by Dirchlet(0.5)

`--global_epochs`: `100`

`--local_epochs`: `10`

`--client_num_in_total`: `10`

`--client_num_per_round`: `2`

`--local_lr`: `1e-2`


| Algo     | Epoch to 50% Acc | Epoch to 60% Acc | Epoch to 70% Acc | Epoch to 80% Acc | Test Acc |
| -------- | ---------------- | ---------------- | ---------------- | ---------------- | -------- |
| FedAvg   | 6                | 16               | 30               | 56               | 70.00%   |
| FedProx  | 12               | 14               | 30               | 56               | 66.72%   |
| SCAFFOLD | 6                | 15               | 27               | -                | 53.93%   |
