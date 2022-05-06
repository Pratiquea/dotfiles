# Dotfiles [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

## Table of contents:
- [Configure Vim](#configure-vim)
- [Gnome environment](#installing-gnome)
- [Installing GTK themes](#installing-gtk-themes)
- [Git Setup](#git-setup)
- [Google Chrome Setup](#google-chrome)
- [Nvidia cuda toolkit installation](#nvidia-cuda-toolkit-installation)


### Configure Vim
* Place .vimrc in home directory (i.e. ~/.vimrc) and a.vim in ```~/.vim/bundle/a.vim```
* Install vim-plug (for more info visit (vim-plug github)[https://github.com/junegunn/vim-plug])
  ```
  curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
  https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
  ```
* Install vundle
  ```
  git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
  ```

### Installing Gnome
open the terminal and paste the following commands:

  ```
  sudo add-apt-repository ppa:gnome3-team/gnome3-staging -y && \
  sudo add-apt-repository ppa:gnome3-team/gnome3 -y &&\
  sudo apt update && \
  sudo apt dist-upgrade && \
  sudo apt install gnome gnome-shell
  ```

### Installing GTK themes
* Adapta
  ```
  sudo apt-add-repository ppa:tista/adapta -y
  sudo apt-get update
  sudo apt-get install adapta-gtk-theme 
  ```
* Flat-remix
  ```
  
  ```
### Git setup
1. `` sudo apt-get install git-all ``
2. Create a repository from your browser.
3. Edit ``git config``: 
```shell-script
git config --global user.name "prateek arora"
git config --global user.email prateekarorav2@gmail.com
git config --global core.editor sublime
```
*Check your configuration, do ``git config --list``*
4. Git clone your repository, do `` git clone htttp://github.com/chahatdeep/<repo_name> ``

5. cd <repo_name>

6. `` shell-script &&
git init ``

7. Copy all the files you want to move to the repo.

8. In the repo, do ``git add * ``

9. `` git add LICENSE `` (Optional)

10. `` git commit -m 'initial project version' ``

11. `` git push ``

### Google Chrome
- Setup key with: 
```shell-script
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
```
- Setup repository with: 
```shell-script
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
```
- Setup package with: 
```shell-script
sudo apt-get update 
sudo apt-get install google-chrome-stable
```
[Reference](https://www.ubuntuupdates.org/ppa/google_chrome)

### Nvidia cuda toolkit installation
1. #### Nvidia driver installation
    First, make sure that you have nvidia drivers installed by running the following command:
    ```
    dpkg -l | grep -i nvidia-driver
    ```

    if the nvidia drivers aren't installed, install them by using the following command (replace "465" with the version you want):
    ```
    sudo apt install nvidia-driver-465
    ```
    Reboot the system
    ```
    reboot
    ```
    Verify if the installation was successful
    ```
    nvidia-smi
    ```
    You should be able to see the following output on your terminal:
    ```
     
    +-----------------------------------------------------------------------------+
    | NVIDIA-SMI 465.19.01    Driver Version: 465.19.01    CUDA Version: 11.3     |
    |-------------------------------+----------------------+----------------------+
    | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
    | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
    |                               |                      |               MIG M. |
    |===============================+======================+======================|
    |   0  NVIDIA GeForce ...  On   | 00000000:01:00.0  On |                  N/A |
    | 30%   36C    P8    16W / 350W |    169MiB / 24259MiB |      5%      Default |
    |                               |                      |                  N/A |
    +-------------------------------+----------------------+----------------------+
                                                                               
    +-----------------------------------------------------------------------------+
    | Processes:                                                                  |
    |  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
    |        ID   ID                                                   Usage      |
    |=============================================================================|
    |    0   N/A  N/A      1150      G   /usr/lib/xorg/Xorg                 78MiB |
    |    0   N/A  N/A      1341      G   /usr/bin/gnome-shell               83MiB |
    |    0   N/A  N/A      1908      G   ...mviewer/tv_bin/TeamViewer        4MiB |
    +-----------------------------------------------------------------------------+

    ```

2. #### Uninstall previously installed versions of nvidia cuda toolkit
    This step is crucial for proper installation of nvidia cuda toolkit. Use the following command to remove existing cuda toolkit installation:
    ```
    sudo apt remove cuda-toolkit*
    sudo rm -rf /usr/local/cuda*
    ```
    Remove existing cuda toolkit sources in apt
    ```
    sudo rm /etc/apt/sources.list.d/cuda*
    sudo apt-get autoremove && sudo apt-get autoclean
    ```

3. #### Cuda toolkit installation (finally!!!)
    Browse the version of cuda toolkit you need to install from [CUDA Tookit Archive](https://developer.nvidia.com/cuda-toolkit-archive) and follow the instructions for installation.
    Below are the installation instructions for cuda toolkit 11.1 using local deb file (refer to the archive for recent links if the following commands do not work)
    ```
    wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pin
    sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
    wget https://developer.download.nvidia.com/compute/cuda/11.1.0/local_installers/cuda-repo-ubuntu1804-11-1-local_11.1.0-455.23.05-1_amd64.deb
    sudo dpkg -i cuda-repo-ubuntu1804-11-1-local_11.1.0-455.23.05-1_amd64.deb
    sudo apt-key add /var/cuda-repo-ubuntu1804-11-1-local/7fa2af80.pub
    sudo apt-get update
    sudo apt-get -y install cuda
    ```

4. #### Verify installation
    Navigate to cuda installation (replace 11.1 with your version of cuda):
    ```
    cd /usr/local/cuda-11.1/samples/1_Utilities/deviceQuery
    ```
    if you are unable to find the deviceQuery directory, do so by using the following command and navigate to the directory:
    ```
    find -iname "deviceQuery"
    ```
    Make and run deviceQuery
    ```
    make
    ./deviceQuery
    ```
    This should output a lot of details including (we care about the following only): 
      * the detected device 
      * CUDA Runtime Version
      * Result (should be PASS)


5. #### Setup environment variables
    Add the following lines to your ~/.bashrc:
    ```
    export PATH=${PATH}:/usr/local/cuda-11.1/bin
    export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/local/cuda-11.1/lib64
    ```

#### Troubleshooting Installation
- Type ``` nvidia-smi ``` in the terminal to check if the nvidia-driver is installed properly.
Reboot the system, if you see the following error: ```NVIDIA NVML Driver/library version mismatch```.
- Upon rebooting, if the system doesn't boot gui, do the following:
  - open a session by pressing ``` ctrl + alt + F2 ```
  - check nvidia driver version ``` dpkg -l | grep -i nvidia ```
  - if the driver version is not the same one as you installed earlier, remove the existing driver and install the one that you know is compatible with your cuda version.
