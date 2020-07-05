# torch

## pytorch编译方法
#### Install Dependencies
Common
```
conda install numpy pyyaml mkl mkl-include setuptools cmake cffi typing
```
On Linux
```bash
# Add LAPACK support for the GPU if needed
conda install -c pytorch magma-cuda90 # or [magma-cuda80 | magma-cuda92 | magma-cuda100 ] depending on your cuda version
```
#### Get the PyTorch Source
```bash
git clone -b v1.1.0 --recursive https://github.com/pytorch/pytorch
cd pytorch
```
#### Install PyTorch
On Linux
```bash
python setup.py install
```