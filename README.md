# Coinhunter
Hunting for bitcoin private keys

`make all`

`make gpu=1 CCAP=61 all`




# Tools 

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
g++ -O2 binsort.cpp
For hash160 and keccak160 ```length``` is ```20``` and for xpoint ```length``` is ```32```.
```
binsort.exe
Usage: binsort.exe length infile outfile
```