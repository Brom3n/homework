# anynines Homework

This release assumes you have a Bosh director environment running, see https://bosh.io/docs/bosh-lite/
It will start a nginx-webserver showing an empty page protected by basic authorization.

## update cloud-config

```bash
bosh -e vbox update-cloud-config ~/workspace/bosh-deployment/warden/cloud-config.yml
```

## upload stemcell

```bash
bosh -e vbox upload-stemcell --sha1 3bec82d41f34106a3687386e65e528aa17171080 \
  https://bosh.io/d/stemcells/bosh-warden-boshlite-ubuntu-xenial-go_agent?v=621.82
```

## clone repository

```bash
cd ~/workspace
git clone https://github.com/Brom3n/homework.git
cd homework/bosh/nginx-release
```

## upload release 

```bash
bosh -e vbox upload-release
```

## deploy release

This assumes that you are in the /homework/bosh/nginx-release directory

```bash
bosh -e vbox -d nginx-deploy deploy /example/nginx.yml
```

## test release via curl

```bash
curl -u admin:test http://10.244.0.2
```
