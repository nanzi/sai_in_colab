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
## make validation in colab
```bash
#block 1:download networks
!cd sai_in_colab && mkdir networks
!cd sai_in_colab/networks && curl -OL http://sai.unich.it/networks/d351f06e446ba10697bfd2977b4be52c3de148032865eaaf9efc9796aea95a0c.gz # LZ-157
!cd sai_in_colab/networks && curl -OL http://sai.unich.it/networks/b03edd5216a19ac79033e74214799c3c1d9d91d2077bab121783a398c865c38a.gz # SAI-720
```

```bash
#block 2: absolute path and blank key matter much
!/content/sai_in_colab/validation -g 2 -k /content/sai_in_colab/sai_vs_lz -n /content/sai_in_colab/networks/d351f06e446ba10697bfd2977b4be52c3de148032865eaaf9efc9796aea95a0c.gz -o "-g -p1600 --noponder -t 1 -q -d -r 0 -w" -n /content/sai_in_colab/networks/b03edd5216a19ac79033e74214799c3c1d9d91d2077bab121783a398c865c38a.gz -o "-g -p1600 --noponder -t 1 -q -d -r 0 -w" -- /content/sai_in_colab/sai -- /content/sai_in_colab/sai 
```
