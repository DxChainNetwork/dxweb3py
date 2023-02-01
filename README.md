# dxweb3py
Interacting with DXC by  [Web3.py](https://web3py.readthedocs.io/en/latest/index.html)



> **_NOTE:_**  All code starting with a `$` is meant to run on your terminal. All code starting with a `>>>` is meant to run in a python interpreter, like [ipython](https://pypi.org/project/ipython/).



# Quickstart

1. install [Web3.py](https://web3py.readthedocs.io/en/latest/index.html)

```shell
$ pip install web3
```

2. find a RPC link of DxChain
3. [connect your node with provider](https://web3py.readthedocs.io/en/latest/providers.html#providers)

```python
>>> from web3 import Web3

>>> w3 = Web3(Web3.HTTPProvider("https://<your-rpc-link>"))

>>> w3.isConnected()
True
```

4. inject [geth_poa_middleware](https://web3py.readthedocs.io/en/stable/middleware.html#proof-of-authority)

```python
>>> from web3.middleware import geth_poa_middleware

>>> w3.middleware_onion.inject(geth_poa_middleware, layer=0)
```

5. get block

```python
>>> w3.eth.get_block("latest")
```

6. get transaction

```python
>>> w3.eth.get_transaction("transaction-hash")
```



## Full Code

```python
from web3 import Web3
from web3.middleware import geth_poa_middleware

w3 = Web3(Web3.HTTPProvider("https://<your-rpc-link>"))
w3.middleware_onion.inject(geth_poa_middleware, layer=0)

block = w3.eth.get_block("latest")
print(block)

transaction = w3.eth.get_transaction("transaction-hash")
print(transaction)
```
