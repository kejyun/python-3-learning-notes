# 安裝 Django

## 使用 pip 安裝 Django

> pip install Django

```shell
(custom_env_name) ~/custom_python_project $ pip install Django
Collecting Django
  Downloading Django-1.11.2-py2.py3-none-any.whl (6.9MB)
    100% |████████████████████████████████| 7.0MB 239kB/s
Collecting pytz (from Django)
  Downloading pytz-2017.2-py2.py3-none-any.whl (484kB)
    100% |████████████████████████████████| 491kB 2.7MB/s
Installing collected packages: pytz, Django
Successfully installed Django-1.11.2 pytz-2017.2
```

## 確認專案環境安裝套件版本

> pip freeze

```shell
(custom_env_name) ~/custom_python_project $ pip freeze
Django==1.11.2
pytz==2017.2
```