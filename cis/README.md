[CIS-CAT-Lite v4](https://learn.cisecurity.org/e/799323/l-799323-2019-11-15-3v7x/2mnnf/198825156?h=vuLqyqzZv2qvju521ZICI2dQ36pvqi-vG-hC6OkykxU)

# kube-bench
```bash
$ ./kube-bench --config-dir `pwd`/cfg --config `pwd`/cfg/config.yaml
$ docker run --pid=host -v /etc:/etc:ro -v /var:/var:ro -v $(which kubectl):/usr/local/mount-from-host/bin/kubectl -t aquasec/kube-bench:latest run --targets=master --version 1.20
$ docker run --pid=host -v /etc:/etc:ro -v /var:/var:ro -v $(which kubectl):/usr/local/mount-from-host/bin/kubectl -t aquasec/kube-bench:latest run --targets=master --version 1.20
```




