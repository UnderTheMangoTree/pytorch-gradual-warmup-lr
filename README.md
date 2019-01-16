# pytorch-gradual-warmup-lr

Gradually warm-up(increasing) learning rate in optimizer.
Proposed in 'Accurate, Large Minibatch SGD: Training ImageNet in 1 Hour'.

## Install

```
$ pip install git+https://github.com/ildoonet/pytorch-gradual-warmup-lr.git
```

## Usage

```python
scheduler_plateau = torch.optim.lr_scheduler.ReduceLROnPlateau(optimizer, patience=3, verbose=True)
scheduler_warmup = GradualWarmupScheduler(optimizer, multiplier=8, total_epoch=10, after_schduler=scheduler_plateau)

for epoch in range(train_epoch):
    scheduler_warmup.step()     # 10 epoch warmup, after that schedule as scheduler_plateau
    ...
```