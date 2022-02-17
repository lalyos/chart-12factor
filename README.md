# 12factor chart

This is a helm chart using the [lalyos/12factor](https://hub.docker.com/r/lalyos/12factor) image.
It creates:
- deployment
- service (ClusterIP)
- ingress

## Install Repo

to add the custom hel repo (you need the helm-git repo)
```
helm plugin install https://github.com/aslafy-z/helm-git --version 0.11.1
helm repo add "12factor git+https://github.com/lalyos/chart-12factor@?ref=simple"
```

## Create a helm release
```
helm upgrade -i lunch \
  12factor/chart-12factor \
  --set "title=Lunch Time" \
  --set color=mediumpurple
```

## Custom domain name

The domain name is generated as `releaseName`.`namespace`.`tld`
see template: https://github.com/lalyos/chart-12factor/blob/simple/templates/ingress.yaml#L14

use the `ingress.tld` helm variable
```
...
  --set ingress.tld=hatnem.de
```
