
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

#### Find the mainnet and testnet addresses corresponding to the private keys:
```
compressed, 888**3
uncompressed, 321
uncompressed, 4242424242
```


```python
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
from ecc import S256Point, G

from helper import double_sha256, encode_base58, hash160

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
