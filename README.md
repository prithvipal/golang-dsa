# golang-dsa

https://prithvipal.github.io/golang-dsa/


## Setup Env

### Create Virtual Env

```
python3 -m venv .venv
source .venv/bin/activate
```

### Install Mkdocs
```
.venv/bin/pip install --upgrade pip -q 
.venv/bin/pip install mkdocs mkdocs-material -q
```

### Run Locally
```
mkdocs serve
```

### Deploy

```
mkdocs gh-deploy
```