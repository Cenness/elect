Leader Election for use in scripts
===================================

A trivial modification of the [reference](https://github.com/kubernetes/client-go/blob/master/examples/leader-election/main.go)

Basic usage:
```
curl -L -o e.tgz https://github.com/Cenness/elect/releases/download/1.0.0/elect.tar.gz
tar xf e.tgz && rm -f e.tgz
chmod +x elect && mv elect /opt

/opt/elect \
  -kubeconfig=/path/to/kubeconfig \
  -logtostderr=true \
  -lease-lock-name=example \
  -lease-lock-namespace=default \
  -id=1 &
  
while true; do
  if [ -f example.leader ]; then
    break
  fi
  sleep 4
done

dowork

> example.done
## you should sleep slightly more than elect itself
sleep 6
```

License
-------

Licensed under Apache License version 2.0. See the [`LICENSE`](LICENSE) file for
details.
