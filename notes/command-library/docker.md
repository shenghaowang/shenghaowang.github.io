---
layout: page
title: Docker
permalink: /notes/command-library/docker/
---

- Build docker image from a container

```bash
docker build -t butterscotch:shenghao .
```

- Run process in an isolated container

```bash
docker run \
  -v $(pwd):/project \
  -v /etc/ds-demand-staging-service-account.json:/etc/service-account.json \
  -e GOOGLE_APPLICATION_CREDENTIALS=/etc/service-account.json \
  -w /project butterscotch:shenghao \
  python src/data/online/main.py

docker run \
  -v $(pwd):/project \
  -v /etc/ds-demand-staging-service-account.json:/etc/service-account.json \
  -e GOOGLE_APPLICATION_CREDENTIALS=/etc/service-account.json \
  -w /project butterscotch:shenghao \
  python src/online_allocate/main.py dryrun=False snapshot_date=20230103 > online_allocate.log

docker run \
  -v $(pwd):/project \
  -v /etc/ds-demand-staging-service-account.json:/etc/service-account.json \
  -e GOOGLE_APPLICATION_CREDENTIALS=/etc/service-account.json \
  --env-file ./secret.env \
  -w /project butterscotch:sylvain \
  python src/segment/main.py ss=integration

docker run -i \
  -v $(pwd):/project \
  -v /Users/shenghao.wang/.ssh/ds-demand-staging-service-account.json:/etc/service-account.json \
  -e GOOGLE_APPLICATION_CREDENTIALS=/etc/service-account.json \
  --env-file ./secret.env \
  -w /project butterscotch:shenghao \
  python src/segment/main.py ss=production snapshot_date=20230117
```