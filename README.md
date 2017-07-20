# [pgAdmin 4](https://www.pgadmin.org/) Installation

using these pages as reference
- [Installing pgAdmin 4 on Ubuntu Desktop 16.04](https://kiahosseini.github.io/help/2016/10/18/installing-pgadmin4-ubuntu-16.04.html)
- [5 minutes PgAdmin4 Desktop install guide](https://gist.github.com/ThomasG77/c0769593196ee387c77ed77bb8a3dbe2)


### Install dependencies
```
sudo apt-get install virtualenv python-pip libpq-dev python-dev
```

### Create a virtual environment
```
mkdir -p ~/pgadmin4/
cd ~/pgadmin4
virtualenv venv -p /usr/bin/python2.7
source ./venv/bin/activate/
```

### Download
Check available versions of [pgAdmin 4](https://www.pgadmin.org/download).
```
wget https://ftp.postgresql.org/pub/pgadmin/pgadmin4/v1.6/pip/pgadmin4-1.6-py2.py3-none-any.whl
```

### Install
```
pip install pgadmin4-1.6-py2.py3-none-any.whl
```

### Configure
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

### Test Installation
```
python ./venv/lib/python2.7/site-packages/pgadmin4/pgAdmin4.py
```

### Create Launcher
Create pgAdmin4.sh and pgAdmin4.desktop files

**~/pgadmin4/pgAdmin4.sh**
```
#! /bin/sh
source ~/pgadmin4/venv/bin/activate
python ~/pgadmin4/venv/local/lib/python2.7/site-packages/pgadmin4/pgAdmin4.py &
sleep 5; sensible-browser http://127.0.0.1:5050
```

**~/.local/share/applications/pgAdmin4.desktop**
```
[Desktop Entry]
Name=pgAdmin 4
Exec=~/apps/pgadmin4/pgAdmin4.sh
Icon=~/apps/pgadmin4/pgadmin.svg
Type=Application
Categories=Database
Terminal=false
```
