Kubernetes
==========

### Contexts

Get contexts,

```
kubectl config get-contexts
```

Use context,

```
kubectl config use-context mycontext
```

Set a default namespace for the current context. 

```
kubectl config set-context --current --namespace mynamespace
```


