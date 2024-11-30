[![Travis](https://travis-ci.com/hichamjanati/pyldpc.svg?branch=master)](https://travis-ci.com/hichamjanati/pyldpc)
[![AppVeyor](https://ci.appveyor.com/api/projects/status/l7g6vywwwuyha49l?svg=true)](https://ci.appveyor.com/project/hichamjanati/pyldpc)
[![Codecov](https://codecov.io/gh/hichamjanati/pyldpc/branch/master/graph/badge.svg)](https://codecov.io/gh/hichamjanati/pyldpc)

# Simulation of LDPC Codes & Applications
*version 0.7.9*

## Description

- Simulation of regular LDPC codes.
- Probabilistic decoding: Belief Propagation algorithm for gaussian white noise transmission.
- Simulation application to image and audio data.

### **Image coding-decoding example:**

![Image example](https://media.giphy.com/media/l4KicsAauqIWjeFR6/giphy.gif)
![Image example](https://media.giphy.com/media/l0COHC49bK6g7yIPm/giphy.gif)

An example of coding-decoding is available at [the pyldpc webpage](https://hichamjanati.github.io/pyldpc/).

## Installation

```bash
pip install git+https://github.com/tubo213/pyldpc.git
```

## Example

```python
import numpy as np
from pyldpc import make_ldpc, encode, decode, get_message

n = 15
d_v = 4
d_c = 5
snr = 20
H, G = make_ldpc(n, d_v, d_c, systematic=True, sparse=True)
k = G.shape[1]
v = np.random.randint(2, size=k)
y = encode(G, v, snr)
d = decode(H, y, snr)
x = get_message(G, d)
assert abs(x - v).sum() == 0
```

## Documentation

For more examples, see [the pyldpc webpage](https://hichamjanati.github.io/pyldpc/).