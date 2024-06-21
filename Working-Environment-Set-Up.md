# Working Environment Set-up Memo for Data Scientist

- [Working Environment Set-up Memo for Data Scientist](#working-environment-set-up-memo-for-data-scientist)
  - [Basic Tools Installation and Set-up](#basic-tools-installation-and-set-up)
    - [Mac Set-up](#mac-set-up)
    - [Python](#python)
    - [Install MiniConda(Recommended) / Conda / Anaconda](#install-minicondarecommended--conda--anaconda)
    - [Install PyTorch/Tensorflow](#install-pytorchtensorflow)
  - [Use Jupyter Notebook](#use-jupyter-notebook)
    - [R Set-up](#r-set-up)
  - [Developer's Tookits](#developers-tookits)
    - [VS Code Setup](#vs-code-setup)
    - [Git](#git)
    - [Terminal/Linux Macine Set-up](#terminallinux-macine-set-up)
  - [DevBox(Internal)](#devboxinternal)
    - [Log in](#log-in)
    - [Use Jupyter on Remote Machine](#use-jupyter-on-remote-machine)
  - [Resources](#resources)

## Basic Tools Installation and Set-up

> - [Reference](https://bytedance.larkoffice.com/wiki/FR6nwTayYi0CzakC0KbctchonLd)

### Mac Set-up

1. set up [iterms2](https://iterm2.com/downloads.html)
2. use zsh
   1. [difference between bash ans zsh](https://unix.stackexchange.com/questions/38172/are-all-bash-scripts-compatible-with-zsh)
   2. [use zsh for $SHELL](https://support.apple.com/zh-cn/102360)
3. install[oh-my-zsh](https://ohmyz.sh/)
   1. There is the oh-my-zsh configuration framework for zsh, which can help simplify the configuration of zsh, providing convenient plugin management and theme configuration functions.
4. install [Homebrew](https://brew.sh/)
5. Install developer toolkits
   1. Command Line Tools is a toolkit containing many commonly used software, such as Git, GCC, Clang, etc. If the system does not prompt you automatically, you can manually trigger the pop-up window and install it with the following command.
   
```bash
# Display the list of valid login shells on the system
cat /etc/shells

# Change the current user's default shell to zsh
chsh -s /bin/zsh

# Download and run the Oh My Zsh installation script from GitHub
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Install Xcode command line tools (for macOS development)
xcode-select --install

# Check the installed version of Git
git version
```

### Python

<https://www.datacamp.com/tutorial/setting-up-vscode-python>

On Linux

```bash
sudo apt update
sudo apt install build-essential
sudo apt install python3.11

```


### [Install MiniConda(Recommended) / Conda / Anaconda](https://towardsdatascience.com/managing-project-specific-environments-with-conda-b8b50aa8be0e)

Install [Miniconda](https://docs.anaconda.com/free/miniconda/)

```bash
# Create directory and download Miniconda installation script
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh

# Run the installation script
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3

# Remove the installation script
rm -rf ~/miniconda3/miniconda.sh

```

Run Conda

```bash
# Initialize conda (add conda to your shell's PATH)
~/miniconda3/bin/conda init

# Create a new conda environment named 'd2l' with Python 3.11
conda create --name d2l python=3.11 -y

# Activate the 'd2l' conda environment
conda activate d2l

```

### Install PyTorch/Tensorflow

Install [Pytorch](https://pytorch.org/get-started/locally/#anaconda)

```bash
conda install pytorch torchvision -c pytorch
# or 
pip3 install torch torchvision
```

Install[Tensorflow2](https://www.tensorflow.org/install)

```bash
conda install tensorflow
# or
pip install tensorflow
```

optional: install d2l

```bash
pip install d2l==0.17.6 #chinese
pip install d2l==1.0.3 # Eng
mkdir d2l-en && cd d2l-en
curl https://d2l.ai/d2l-en-1.0.3.zip -o d2l-en.zip
unzip d2l-en.zip && rm d2l-en.zip
cd pytorch # or tensowflow

```

## Use Jupyter Notebook

Install [Jupyter Notebook](https://test-jupyter.readthedocs.io/en/latest/install.html)

```bash
conda install jupyter
```

Set-up

```bash
pip install  jupyterthemes -i <https://pypi.tuna.tsinghua.edu.cn/simple>

# reference : https://bbs.huaweicloud.com/blogs/314114>

jt -t gruvboxd -fs 11 -cellw 85% -ofs 12 -dfs 11 -T

#jt -l 可以看所有可用主题

# 扩展功能：
pip install jupyter_contrib_nbextensions -i <https://pypi.tuna.tsinghua.edu.cn/simple>
jupyter contrib nbextension install --sys-prefix

```

use [config](https://jupyter-notebook.readthedocs.io/en/5.7.4/config.html)

```bash
# Defaults for these options can also be set by creating a file named jupyter_notebook_config.py in your Jupyter folder. The Jupyter folder is in your home directory, ~/.jupyter.

jupyter notebook --generate-config

```

change the following lines in config

```plaintext
c.NotebookApp.iopub_data_rate_limit = 1000000000
c.NotebookApp.ip = "*"
# on remote machine
c.NotebookApp.open_browser=False
# change to a separate file
c.NotebookApp.notebook_dir = 'home/liuxinhe.x/jupyter
```

further reading 

- https://www.jianshu.com/p/21ba32a057c4
- [Notebook 7](https://jupyter-notebook.readthedocs.io/en/latest/migrate_to_notebook7.html)

### R Set-up

1. [Install R & R Studio](https://posit.co/download/rstudio-desktop/)
2. R kernel for Jupyter : <https://github.com/IRkernel/IRkernel>

## Developer's Tookits



### VS Code Setup

1. download [VS Code](https://code.visualstudio.com/)
2. download VS Code Extensions
   1. install [Python Extension Pack](https://marketplace.visualstudio.com/items?itemName=donjayamanne.python-extension-pack) which includes
   2. Python - Linting, Debugging (multi-threaded, remote), Intellisense, code formatting, refactoring, unit tests, snippets, Data Science (with Jupyter), PySpark and more.
   3. Jinja
   4. Django
   5. [IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode)
   6. Python Environment Manager - Provides the ability to view and manage all of your Python environments & packages from a single place.
   7. Python Docstring Generator - Quickly insert Python comment blocks with contextually inferred parameters for classes and methods based on multiple, selectable template patterns.
   8. Python Indent - Correct python indentation in Visual Studio Code.
   9. [Jupyter](https://github.com/microsoft/vscode-jupyter)
   10. install [PyLance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
   11. [CodeSnap](https://marketplace.visualstudio.com/items?itemName=adpyke.codesnap) or CodeSnap plus
   12. Path Intellisense: autocomplete file paths
   13. Themes: Search themes for example, "Atom" in the marketplace and use settings
3. Settings
   1. Jupyter › Interactive Window › Text Editor: Execute Selection -> Yes
   2. Command + Shift + P -> install code command in PATH, then you can use "code xxx" to open files in command line

### Git

1. Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
2. [First Time Setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

### Terminal/Linux Macine Set-up

## DevBox(Internal)

> By ByteDance
>
> - [Reference](https://bytedance.larkoffice.com/docx/doxcnakd2wuDocg7uzV2HyxuZJh)

- [DevBox Home](https://cloud-boe.bytedance.net/devbox/home)
- [CUDA安装](https://bytedance.larkoffice.com/docx/doxcn6K4DCHarR0tjhBdB0YzcXf)
- [PaddlePaddle安装](https://bytedance.larkoffice.com/wiki/wikcnuNqvseH1pFyxHO03yEXHDf)

### Log in

1. Set-up Config in ~/.ssh/config

   ```bash
   Host *
        GSSAPIAuthentication yes
        GSSAPIDelegateCredentials no
        HostKeyAlgorithms +ssh-rsa
        PubkeyAcceptedKeyTypes +ssh-rsa
   ```

2. Log-in using [Kerboros](https://documentation.suse.com/zh-cn/sles/15-SP2/html/SLES-all/cha-security-kerberos.html)

    ```bash

    kinit liuxinhe.x@BYTEDANCE.COM 
    # input pass code
    ssh liuxinhe.x@10.37.73.163
    # SSH link to remote, IP：10.37.73.163/8888
    ```

### Use Jupyter on Remote Machine

- [Reference](https://bytedance.larkoffice.com/wiki/wikcnYJGnpzyZbphyiqEqp0tafg)


- 自己的IP: <http://210.22.150.146:8888>
- 开发机:<http://10.37.73.163:8888>

Open Jupyter 

```bash
'''
Run Jupyter Notebook with nohup in the background and log output to a file.
The command below starts Jupyter Notebook on IP 0.0.0.0 and saves the output to /home/liuxinhe.x/jupyter.log

When you use nohup before a command, it prevents the command from receiving the hangup signal (SIGHUP) that is normally sent to terminal-bound processes when the controlling terminal is disconnected. 
'''

nohup jupyter notebook --allow-root --ip=0.0.0.0 > /home/liuxinhe.x/jupyter.log &

```

Close Jupyter

```bash
ps -aux|grep jupyter
kill -9 2326523
```

## Resources

<https://stackoverflow.com/>
<https://discourse.jupyter.org/>
<https://www.python.org/community/forums/>
<https://docs.jupyter.org/en/latest/>
<https://www.markdownguide.org/basic-syntax/>
