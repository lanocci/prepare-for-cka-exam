# Basic Usage

- 指定したノード上で動くPodを停止してノード自体を落とす
  - `kubectl drain ${node name}`

# Options

- 強制的にdrainする
  - `--force`
    - *volume を持っているノードはdrainできない*

> https://kubernetes-v1-4.github.io/docs/user-guide/kubectl/kubectl_drain/
> https://kubernetes.io/docs/tasks/administer-cluster/safely-drain-node/
> https://qiita.com/tkusumi/items/946b0f31931d21a78058
