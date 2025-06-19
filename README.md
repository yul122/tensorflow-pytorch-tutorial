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
Here are some tips to copy your files from your laptop to the server:
```python
scp /path/of/file/in/your/laptop/ yourname@tau-neutrino.ps.uci.edu:/home/yourname/nova/pytorch_version

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

## Testing

Ater the trainning, you will see ".pt" files in your "models" directory. 
Run the command to save your file in ".pkl" file.

```python
python test2.py --modelpath /home/yournme/nova/pytorch_version/models/your_pt_file.pt --path /path/you/used/in/training --name name_you_wanna_to_give_for_model
```
For example:
```python
python test2.py --modelpath /home/yuechen/nova/pytorch_version/models/train_tau_pytorch_checkpoint.pt --path /mnt/ironwolf_20t/users/yuechen/data/after_process_Jan10 --name pytorch_tau_test_29
```
# Plot
Remotely, run jupyter notebook --no-browser --port=8889
Locally, run ssh -N -f -L localhost:8888:localhost:8889 remote_user@remote_host


