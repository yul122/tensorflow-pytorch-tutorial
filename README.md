# General Setup
First, you have to setup your base
```python
base = "/home/yourname/nova" 
```
For example, my base is like: /home/yuechen/nova
## Python version
If you are running code on Muon server, you have to double-check if you have python3.6

# Run 
Our example data directory on the server: /mnt/ironwolf_20t/users/yuechen/data/after_process_Jan10
## Setup befor run
```python
cd /home/yourname/nova
mkdir pytorch_version
cd pytorch_version
```
After that, Put all the files in the root directory named pytorch_version. Then your base is looking like this:
```python
-nova
    \
     pytorch_version
     ... ...
                    \
                    Googlenet_Regression.py
                    Mobilenet_Regression.py
                    Preprocessed_Pytorch.py
                    test2.py
                    train2.py


```



