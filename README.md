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
mkdir models
mkdir pkl_file
```
After that, put all the files in my package into the root directory named pytorch_version. Then your base is looking like this:
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
                    models
                    pkl_file

```
## Run command
```python
python train2.py --path /path/to/data/,/you/can/use/example/path/above --model model --name name_you_wanna_to_give | tee name_of_log_you_wanna_to_give.log
```
As it is shown above, path is the path to data. 
Model means different CNNs you are going to use to train model. Currently, we only have mobilenet and googlenet. So in this part, the command is either "--model googlenet", or "--model mobilenet".
Name is the name you want to give to the result.
you can also name the output log.

For example:
```python
python train2.py --path /mnt/ironwolf_20t/users/yuechen/data/after_process_Jan10 --model googlenet --name train_tau_pytorch | tee train_tau_pytorch_29th_May.log
```



