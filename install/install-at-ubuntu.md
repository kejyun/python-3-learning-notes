# 在 Ubuntu 安裝 Python 3

## 安裝相依性套件

```
sudo apt-get install build-essential
sudo apt-get install libbz2-dev libreadline-dev libsqlite3-dev
sudo apt-get install libssl-dev
```

## 安裝 pyenv

```
curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash
```

安裝示意流程

```shell
curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  2099  100  2099    0     0   3069      0 --:--:-- --:--:-- --:--:--  3068
Cloning into '/home/vagrant/.pyenv'...
remote: Counting objects: 569, done.
remote: Compressing objects: 100% (432/432), done.
remote: Total 569 (delta 226), reused 254 (delta 48), pack-reused 0
Receiving objects: 100% (569/569), 251.02 KiB | 146.00 KiB/s, done.
Resolving deltas: 100% (226/226), done.
Checking connectivity... done.
Cloning into '/home/vagrant/.pyenv/plugins/pyenv-doctor'...
remote: Counting objects: 11, done.
remote: Compressing objects: 100% (8/8), done.

▽
export PATH="/home/vagrant/.pyenv/bin:$PATH"
remote: Total 11 (delta 1), reused 6 (delta 1), pack-reused 0
Unpacking objects: 100% (11/11), done.
Checking connectivity... done.
Cloning into '/home/vagrant/.pyenv/plugins/pyenv-installer'...
remote: Counting objects: 17, done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 17 (delta 2), reused 10 (delta 0), pack-reused 0
Unpacking objects: 100% (17/17), done.
Checking connectivity... done.
Cloning into '/home/vagrant/.pyenv/plugins/pyenv-update'...
remote: Counting objects: 7, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 7 (delta 1), reused 5 (delta 1), pack-reused 0
Unpacking objects: 100% (7/7), done.
Checking connectivity... done.
Cloning into '/home/vagrant/.pyenv/plugins/pyenv-virtualenv'...
remote: Counting objects: 54, done.
remote: Compressing objects: 100% (48/48), done.
remote: Total 54 (delta 11), reused 16 (delta 0), pack-reused 0
Unpacking objects: 100% (54/54), done.
Checking connectivity... done.
Cloning into '/home/vagrant/.pyenv/plugins/pyenv-which-ext'...
remote: Counting objects: 10, done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 10 (delta 1), reused 5 (delta 0), pack-reused 0
Unpacking objects: 100% (10/10), done.
Checking connectivity... done.

WARNING: seems you still have not added 'pyenv' to the load path.

# Load pyenv automatically by adding
# the following to ~/.bash_profile:

export PATH="/home/vagrant/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

## 設定 terminal 環境變數

在安裝 pyenv 結束後會看到要求你將設定寫入 `.bash_profile`，讓 terminal 連線進去後能夠預先載入相關環境設定

```shell
WARNING: seems you still have not added 'pyenv' to the load path.

# Load pyenv automatically by adding
# the following to ~/.bash_profile:

export PATH="/home/vagrant/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

所以將下列三行寫到家目錄下的 `.bash_profile` 檔案中

```shell
export PATH="/home/vagrant/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```


重新登入 terminal 載入 pyenv 設定

或使用 `source ~/.bash_profile` 也可以讀取到最新的設定


## pyenv 已安裝 python 版本清單

> pyenv versions

```shell
$ pyenv versions
* system (set by /home/vagrant/.pyenv/version)
  3.5.2
  3.5.2/envs/custom_env_name
```

## 列出所有可以安裝的 python 版本

> pyenv install -l

```shell
$ pyenv install -l
Available versions:
  2.1.3
  2.2.3
  2.3.7
  2.4
  2.4.1
  2.4.2
  2.4.3
  2.4.4
  2.4.5
  2.4.6
  ...
  ...
  ...
  3.4.3
  3.4.4
  3.4.5
  3.4.6
  3.5.0
  3.5-dev
  3.5.1
  3.5.2
  3.5.3
  3.6.0
  3.6-dev
  3.6.1
  3.7-dev
```

## 安裝指定版本 Python（此為安裝 3.5.2 版本）

> pyenv install 3.5.2

```shell
$ pyenv install 3.5.2
Downloading Python-3.5.2.tar.xz...
-> https://www.python.org/ftp/python/3.5.2/Python-3.5.2.tar.xz
Installing Python-3.5.2...
patching file Lib/venv/scripts/posix/activate.fish

WARNING: The Python bz2 extension was not compiled. Missing the bzip2 lib?
Installed Python-3.5.2 to /home/vagrant/.pyenv/versions/3.5.2
```

## 設定虛擬環境

> pyenv virtualenv 3.5.2 custom_env_name

中間為該環境使用的 Python 版本，最後為該版本的名稱

```shell
$ pyenv virtualenv 3.5.2 custom_env_name
Ignoring indexes: https://pypi.python.org/simple
Requirement already satisfied (use --upgrade to upgrade): setuptools in /home/vagrant/.pyenv/versions/3.5.2/envs/custom_env_name/lib/python3.5/site-packages
Requirement already satisfied (use --upgrade to upgrade): pip in /home/vagrant/.pyenv/versions/3.5.2/envs/custom_env_name/lib/python3.5/site-packages
```

## 建立專案目錄，並指定該裝案要使用的 python 版本

```shell
~$ mkdir custom_python_project
$ cd custom_python_project
~/custom_python_project $ pyenv local custom_env_name
(custom_env_name) ~/custom_python_project $
```

## python 版本設定檔 `.python-version`

```shell
(custom_env_name) ~/custom_python_project $ ls -al
total 4
drwxr-xr-x 1 vagrant vagrant  102 Jun  5 05:01 .
drwxr-xr-x 1 vagrant vagrant 1462 Jun  5 05:01 ..
-rw-r--r-- 1 vagrant vagrant   10 Jun  5 05:01 .python-version

(custom_env_name) ~/custom_python_project $ cat .python-version
custom_env_name
```

不同的專案因應專案套件使用的不同，可以同時使用不同版本的 Python