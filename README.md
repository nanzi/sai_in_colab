# sai_in_colab

```bash
# Block 1
!git clone https://github.com/nanzi/sai_in_colab
!nvidia-smi -L
!cd sai_in_colab && chmod +x sai autogtp
!ls -alh
```

```bash
#block 2
#The -g parameter changes the number of parallel games, the -m parameter limits the maximum number of training games 
!cd sai_in_colab && ./autogtp --url http://sai.unich.it/ --username $YOURUSERNAME --password $YOURPASSWORD -g3 -m100 | grep minute
```

## compile in colab
```bash
!git clone --recursive https://github.com/sai-dev/sai 
!cd sai && git checkout sai-0.18
!cd sai && mkdir build
!cd sai/build && cmake ..
!cd sai/build && cmake --build .
```
