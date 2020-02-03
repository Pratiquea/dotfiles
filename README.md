# Dotfiles [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

## Table of contents:
- [Gnome environment](#Installing-Gnome)
- [Installing GTK themes](#Installing-GTK-themes)
- [Git Setup](#git-setup)
- [Google Chrome Setup](#google-chrome)



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
### Git setup:
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

### Google Chrome:
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
