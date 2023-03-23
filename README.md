# Robotics Transformer

## Tips

1. pay attention to the package version while `pip install`, my recipe as below, especially for the first part
2. some minor code changes in this repo
3. Install `tensor2robot` and put `t2r_pb2.py` in `tensor2robot/proto/`, or generate compiled code on your own with [protoc](https://protobuf.dev/reference/python/python-generated/)


```bash
# packages in environment at /home/nirj/miniconda3/envs/RT1:
#
# Name                    Version                   Build  Channel

python                    3.7.12          hf930737_100_cpython    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
tensorflow                1.15.5                   pypi_0    pypi
tensorflow-probability    0.7.0                    pypi_0    pypi
tf-agents                 0.3.0                    pypi_0    pypi
gast                      0.2.2                    pypi_0    pypi
gin                       0.1.6                    pypi_0    pypi
gin-config                0.1.3                    pypi_0    pypi
protobuf                  3.19.0                   pypi_0    pypi

_libgcc_mutex             0.1                 conda_forge    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
_openmp_mutex             4.5                       2_gnu    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
absl-py                   1.4.0                    pypi_0    pypi
astor                     0.8.1                    pypi_0    pypi
bzip2                     1.0.8                h7f98852_4    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
ca-certificates           2022.12.7            ha878542_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
cloudpickle               2.2.1                    pypi_0    pypi
decorator                 5.1.1                    pypi_0    pypi
dm-tree                   0.1.8                    pypi_0    pypi
google-pasta              0.2.0                    pypi_0    pypi
grpcio                    1.51.3                   pypi_0    pypi
gym                       0.23.0                   pypi_0    pypi
gym-notices               0.0.8                    pypi_0    pypi
h5py                      2.10.0                   pypi_0    pypi
importlib-metadata        6.1.0                    pypi_0    pypi
keras-applications        1.0.8                    pypi_0    pypi
keras-preprocessing       1.1.2                    pypi_0    pypi
ld_impl_linux-64          2.40                 h41732ed_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
libffi                    3.4.2                h7f98852_5    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
libgcc-ng                 12.2.0              h65d4601_19    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
libgomp                   12.2.0              h65d4601_19    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
libnsl                    2.0.0                h7f98852_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
libsqlite                 3.40.0               h753d276_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
libstdcxx-ng              12.2.0              h46fd767_19    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
libuuid                   2.32.1            h7f98852_1000    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
libzlib                   1.2.13               h166bdaf_4    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
markdown                  3.4.1                    pypi_0    pypi
markupsafe                2.1.2                    pypi_0    pypi
mock                      5.0.1                    pypi_0    pypi
ncurses                   6.3                  h27087fc_1    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
numpy                     1.18.0                   pypi_0    pypi
openssl                   3.1.0                h0b41bf4_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
opt-einsum                3.3.0                    pypi_0    pypi
pillow                    9.4.0                    pypi_0    pypi
pip                       23.0.1             pyhd8ed1ab_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
pygame                    2.1.0                    pypi_0    pypi
readline                  8.1.2                h0f457ee_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
setuptools                67.6.0             pyhd8ed1ab_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
six                       1.16.0                   pypi_0    pypi
sqlite                    3.40.0               h4ff8645_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
tensorboard               1.15.0                   pypi_0    pypi
tensorflow-estimator      1.15.1                   pypi_0    pypi
termcolor                 2.2.0                    pypi_0    pypi
tk                        8.6.12               h27826a3_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
typing-extensions         4.5.0                    pypi_0    pypi
werkzeug                  2.2.3                    pypi_0    pypi
wheel                     0.40.0             pyhd8ed1ab_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
wrapt                     1.15.0                   pypi_0    pypi
xz                        5.2.6                h166bdaf_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
zipp                      3.15.0                   pypi_0    pypi

```

*This is not an officially supported Google product.*


This repository is a collection code files and artifacts for running
Robotics Transformer or RT-1.

## Features

* Film efficient net based image tokenizer backbone
* Token learner based compression of input tokens
* Transformer for end to end robotic control
* Testing utilities

## Getting Started

### Installation
Clone the repo
```bash
git clone https://github.com/google-research/robotics_transformer.git
pip install -r robotics_transformer/requirements.txt
python -m robotics_transformer.tokenizers.action_tokenizer.test
```

### Running Tests

To run RT-1 tests, you can clone the git repo and run
[bazel](https://bazel.build/):

```bash
git clone https://github.com/google_research/robotics_transformer.git
cd robotics_transformer
bazel test ...
```

### Using trained checkpoints
Checkpoints are included in trained_checkpoints/ folder for three models:
1. [RT-1 trained on 700 tasks](trained_checkpoints/rt1main)
2. [RT-1 jointly trained on EDR and Kuka data](trained_checkpoints/rt1multirobot)
3. [RT-1 jointly trained on sim and real data](trained_checkpoints/rt1simreal)

They are tensorflow SavedModel files. Instructions on usage can be found [here](https://www.tensorflow.org/guide/saved_model)


## Future Releases

The current repository includes an initial set of libraries for early adoption.
More components may come in future releases.

## License

The Robotics Transformer library is licensed under the terms of the Apache
license.
