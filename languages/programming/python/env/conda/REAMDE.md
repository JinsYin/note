# Conda

Anaconda 的核心是 conda，同时 conda 也是一个包管理器。

## 安装

* [安装 Anaconda](./anaconda-installation.md)
* [安装 Miniconda](./miniconda-installation.md)

## 常用操作

```bash
# 查看安装了哪些软件包及其版本
$ conda list

# 查看某个虚拟环境已安装的软件包
$ conda list -n python2.7

# 查看已安装的软件包的版本信息，或者检查软件包是否被安装
$ conda list pip
Name    Version    Build    Channel
pip     9.0.1      py36h6c6f9ce_4

# 查询所有可安装的软件包，以及可安装的版本
$ conda search

# 查询某个软件包可用的版本
$ conda search python
$ conda search "^python$"

# 安装最新版本的软件包
$ conda install numpydoc

# 安装指定版本的软件包
$ conda install numpydoc=0.6.0

# 更新某个软件包
$ conda update python

# 更新所有软件包
$ conda update

# 删除软件包
$ conda remove <package>
```

> 切勿使用 pip 升级或卸载 conda 安装的软件包；pip 的升级和卸载操作仅限于 pip install 命令安装的软件包

## 虚拟环境

conda 默认的虚拟环境为 `bash`，该环境的路径为：`~/anaconda3`，其他虚拟环境的路径为 `~/anaconda3/envs/<env>`。

```bash
# 查看所有虚拟环境（* 表示当前所在的环境）
$ conda env list # or: conda info --env
base                  *  /home/yin/anaconda3

# 创建虚拟环境（该环境包含 2.7 中最新版本的 python 和最新版本的 numpy）
$ conda create --name python2.7 python=2.7 numpy
```

另外，我当前安装的 Anaconda 使用的 Python 版本为 `3.6`，如果希望默认的 `base` 环境使用 Python `3.5`，可以直接在默认环境下安装想要的 Python 版本：

```bash
# base 环境
$ conda install python=3.5
```

* 切换虚拟环境（命令行）

进入 `python2.7` 环境：

```bash
# Linux & Mac
$ source activate python2.7

# Windows
$ activate python2.7
```

回到默认的 `base` 环境：

```bash
# Linux & Mac（Linux 下执行 'source ~/.bashrc' 也会退回到 base 虚拟环境）
$ source deactivate # or: source deactivate python2.7

# Windows
$ deactivate
```

上面的命令太难记了，试图简化一下（Linux）：

```bash
$ vi ~/.bashrc
alias condaenv='source activate'
alias condaexit='source deactivate'

# 立即生效
$ source ~/.bashrc

# 进入虚拟环境
$ condaenv python2.7

# 退出虚拟环境
$ condaexit
```

* 切换虚拟环境（PyCharm IDE）

`File` -> `Settings` -> `Project` -> `Project Interpreter`

* 删除虚拟环境

```bash
$ conda env remove --name python2.7

# 还可以通过删除该环境下所有的包来实现
$ conda remove --name python2.7 --all
```

## 完美应用

这种方式不仅会安装指定版本的 Python，还会基于指定的 Python 版本来安装 Anaconda 中所有的包。

```bash
% conda create -n python2.7 python=2.7 anaconda
% conda create -n python3.5 python=3.5 anaconda
```

## Conda & pip

Conda 创建虚拟环境时，会为每个 Python 新环境中安装一个 `pip`，此时可以使用 `pip` 或 `conda` 两种方式来安装 Python 包：

* 如果使用 `pip`
  * _base_ 环境安装的包位于 `${ANACONDA_HOME}/lib/<python_version>/site-packages/` 目录
  * 其他虚拟环境安装的包位于 `${ANACONDA_HOME}/envs/<virtualenv_name>/lib/<python_version>/site-packages/` 目录
* 如果使用 `conda`
  * 所有安装的包均位于 `${ANACONDA_HOME}/pkgs/` 目录，每个包可能存在多个版本，每个虚拟环境引用相应版本的包。

当使用 `conda` 和 `pip` 安装同一包时，

## 参考

* [GitHub - conda/conda](https://github.com/conda/conda)
* [Document - conda](https://conda.io/docs/index.html)