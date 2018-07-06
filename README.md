
# Creating Addresses


```python
# Address Example

from helper import encode_base58, hash160, double_sha256
sec = bytes.fromhex('025CBDF0646E5DB4EAA398F365F2EA7A0E3D419B7E0330E39CE92BDDEDCAC4F9BC')
h160 = hash160(sec)
raw = b"\x00" + h160
raw = raw + double_sha256(raw)[:4]
addr = encode_base58(raw)
print(addr)
```

### Try it

#### 7.1. Find the mainnet and testnet addresses corresponding to the private keys:
```
compressed, 888**3
uncompressed, 321
uncompressed, 4242424242
```


```python
# Exercise 7.1
from ecc import G

from helper import double_sha256, encode_base58, hash160

components = (
    # (compressed, secret)
    (True, 888**3),
    (False, 321),
    (False, 4242424242),
)

# iterate through components
    # get the public point
    # get the sec format
    # hash160 the result
    # prepend b'\x00' for mainnet b'\x6f' for testnet
        # raw is the prefix + h160
        # get the double_sha256 of raw, first 4 bytes are the checksum
        # append checksum
        # encode_base58 the whole thing
```

### Test Driven Exercise


```python
from ecc import S256Point

G = S256Point(
    0x79be667ef9dcbbac55a06295ce870b07029bfcdb2dce28d959f2815b16f81798,
    0x483ada7726a3c4655da4fbfc0e1108a8fd17b448a68554199c47d08ffb10d4b8)

class S256Point(S256Point):

    def address(self, compressed=True, testnet=False):
        '''Returns the address string'''
        # get the sec
        # hash160 the sec
        # raw is hash 160 prepended w/ b'\x00' for mainnet, b'\x6f' for testnet
        # checksum is first 4 bytes of double_sha256 of raw
        # encode_base58 the raw + checksum
        # return as a string, you can use .decode('ascii') to do this.
        pass
```

### Creating addresses

#### 8.1. Create a testnet address using your own secret key
#### (use your phone number if you can't think of anything)
#### Record this secret key!


```python
# Exercise 8.1
from ecc import G

# use your phone number if you can't think of anything

# get the public point
# if you completed 7.2, just do the .address(testnet=True) method on the public point
```
