Leader Election for use in scripts
===================================

A trivial modification of the [reference](https://github.com/kubernetes/client-go/blob/master/examples/leader-election/main.go)

Basic usage:
```
go run main.go -kubeconfig=/path/to/kubeconfig -logtostderr=true -lease-lock-name=example -lease-lock-namespace=default -id=1 &

while true; do
  if [ -f example.leader ]; then
    break
  fi
  sleep 4
done

dowork

> example.done
sleep 1
```

License
-------

Licensed under Apache License version 2.0. See the [`LICENSE`](LICENSE) file for
details.
