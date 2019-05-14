# torchgpipe

[![Build Status](https://travis-ci.org/kakaobrain/torchgpipe.svg?branch=master)](https://travis-ci.org/kakaobrain/torchgpipe)

A [GPipe](https://arxiv.org/abs/1811.06965) implementation in PyTorch.

## How to use

Prerequisites are:

- Python 3.6+
- PyTorch 1.0

Install via PyPI:

```sh
$ pip install torchgpipe
```

Wrap your `nn.Sequential` module with `torchgpipe.GPipe`. You have to specify
`balance` to partition the module. Then you can specify the number of
micro-batches with `chunks`:

```python
from torchgpipe import GPipe

model = nn.Sequential(a, b, c, d)
model = GPipe(model, balance=[1,1,1,1], chunks=8)

for input in data_loader:
    outputs = model(input)
```

---

This project is still under development. Any public API would be changed
without deprecation warnings until v0.1.0.
