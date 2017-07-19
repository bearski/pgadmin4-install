## [pgadmin4](https://www.pgadmin.org/) installation

using these pages as reference
- [Installing pgAdmin 4 on Ubuntu Desktop 16.04](https://kiahosseini.github.io/help/2016/10/18/installing-pgadmin4-ubuntu-16.04.html)
- [5 minutes PgAdmin4 Desktop install guide](https://gist.github.com/ThomasG77/c0769593196ee387c77ed77bb8a3dbe2)


#### Install dependencies
```
sudo apt-get install virtualenv python-pip libpq-dev python-dev
```
#### Create a virtual environment
```
mkdir -p ~/pgadmin4/
cd ~/pgadmin4
virtualenv venv -p /usr/bin/python2.7
source ./venv/bin/activate/
```
#### Download
Check available versions of [pgAdmin 4 (Python Wheel)](https://www.pgadmin.org/download/pgadmin-4-python-wheel/).
```
wget https://ftp.postgresql.org/pub/pgadmin/pgadmin4/v1.6/pip/pgadmin4-1.6-py2.py3-none-any.whl
```
#### install
```
pip install pgadmin4-1.6-py2.py3-none-any.whl
```
#### Configure
```
echo "# coding: utf-8
from config import *

SERVER_MODE = False

# Secret key for signing CSRF data. Override this in config_local.py if
# running on a web server
CSRF_SESSION_KEY = 'MyAlternateSuperSecret1'

# Secret key for signing cookies. Override this in config_local.py if
# running on a web server
SECRET_KEY = 'MyAlternateSuperSecret2'

# Salt used when hashing passwords. Override this in config_local.py if
# running on a web server
SECURITY_PASSWORD_SALT = 'MyAlternateSuperSecret3'
" > ./venv/lib/python2.7/site-packages/pgadmin4/config_local.py
```
