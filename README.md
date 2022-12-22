# Coinhunter
Hunting for bitcoin/ethereum private keys

Building CPU-ONLY Version:

`make all`

Building CUDA-SUPPORTED Version:

`make gpu=1 CCAP=N all`
Where N is your CUDA device compute capability.


```
Coinhunter [OPTIONS] [TARGETS]

-h, --help                               : Display this help message
-v, --version                            : Show Coinhunter version
-c, --check                              : Check if the system works
-u, --uncomp                             : Search uncompressed points
-b, --both                               : Search both uncompressed or compressed points
-g, --gpu                                : Enable GPU calculation
-l, --list                               : List all cuda available devices
-i, --in FILE                            : Read rmd160 hashes or xpoints from FILE, it should be in sorted binary format
-o, --out FILE                           : Write found keys to FILE, default: Found.txt
-m, --mode MODE                          : Specify search mode ADDRESS, ADDRESSES, XPOINT, XPOINTS
-t, --thread N                           : Specify number of CPU thread, default is number of cores available
-r, --rkey Rkey                          : Random key interval in MegaKeys, default is disabled
--range 1:ffff                           : Specify the keyspace range to search in
--coin BTC/ETH                           : Specify Coin name to search. ETH supports only ADDRESS and ADDRESSES modes.
--gpui 0, 1, 2                           : List of GPU(s) to use, default is 0
--gpux g0x, g0y                          : Specify GPU(s) kernel gridsize, default is 8*(Device MP count)
```
# Example usage
Trying our luck on puzzle 66:

`./Coinhunter -t 0 -g --gpui 0 --gpux 256,256 -m address --coin BTC -o Found.txt --range 20000000000000000:3ffffffffffffffff 13zb1hQbWVsc2S7ZTZnP2G4undNNpdh5so`

Brute Forcing a list of addresses using GPU in 160-bit range:

`./Coinhunter -t 0 -g --gpui 0 --gpux 256,256 -m addresses --coin BTC -o Found.txt --range 8000000000000000000000000000000000000000:ffffffffffffffffffffffffffffffffffffffff --in addr.txt`

## addr-to-hash160.py
```
python addr-to-hash160.py.py addr.txt hash160.bin
```

## pubkeys-to-xpoints.py
```
python pubkeys-to-xpoints.py pubkeys.txt xpoints.bin
```

## eth-addr-to-bin.py
```
python eth-addr-to-bin.py addr.txt addr.bin
```

## Binsort
Compile/Build `g++ -O2 binsort.cpp`

For hash160 and keccak160 ```length``` is ```20``` and for xpoint ```length``` is ```32```.
```
binsort.exe
Usage: binsort.exe length infile outfile
```
