some kind of issue with raven idk why but it has bunch of weird failings
there are some other issues with helpdesk that says: "Socket Connection Error xhr poll error"
idk if I even need translator?

```
git clone https://github.com/frappe/frappe_docker && cd frappe_docker
export APPS_JSON='[
  {
    "url": "https://github.com/frappe/erpnext",
    "branch": "version-15"
  },
  {
    "url": "https://github.com/frappe/hrms",
    "branch": "version-15"
  },
  {
    "url": "https://github.com/frappe/payments",
    "branch": "version-15"
  },
  {
    "url": "https://github.com/frappe/webshop",
    "branch": "version-15"
  },
  {
    "url": "https://github.com/frappe/helpdesk",
    "branch": "main"
  },
  {
    "url": "https://github.com/frappe/ecommerce_integrations",
    "branch": "main"
  },
  {
    "url": "https://github.com/The-Commit-Company/Raven",
    "branch": "main"
  },
  {
    "url": "https://github.com/frappe/translator",
    "branch": "master"
  },
  {
    "url": "https://github.com/frappe/wiki",
    "branch": "master"
  }
]'
export APPS_JSON_BASE64=$(echo ${APPS_JSON} | base64 -w 0)
docker build --no-cache \
  --build-arg=FRAPPE_PATH=https://github.com/frappe/frappe \
  --build-arg=FRAPPE_BRANCH=version-15 \
  --build-arg=PYTHON_VERSION=3.11.6 \
  --build-arg=NODE_VERSION=18.18.2 \
  --build-arg=APPS_JSON_BASE64=$APPS_JSON_BASE64 \
  --tag=custom/hrms:1.0.0 \
  --file=images/custom/Containerfile .
```


```
sudo docker login -u gioe1996
```

```
sudo docker tag custom/hrms:1.0.0 gioe1996/test-erpnext:latest
```

```
sudo docker push gioe1996/test-erpnext:latest
```
