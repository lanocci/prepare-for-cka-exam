# daemonset で各 node に pod を配置しなさい

```fluentd-elasticsearch.yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: fluentd-elasticsearch
  namespace: kube-system
  labels:
    k8s-app: fluentd-logging
spec:
  selector:
    matchLabels:
      name: fluentd-elasticsearch
  template:
    metadata:
      labels:
        name: fluentd-elasticsearch
    spec:
      tolerations:
      - key: node-role.kubernetes.io/master
        effect: NoSchedule
      containers:
      - name: fluentd-elasticsearch
        image: gcr.io/google-containers/fluentd-elasticsearch:1.20
        resources:
          limits:
            memory: 200Mi
          requests:
            cpu: 100m
            memory: 200Mi
        volumeMounts:
        - name: varlog
          mountPath: /var/log
        - name: varlibdockercontainers
          mountPath: /var/lib/docker/containers
          readOnly: true
      terminationGracePeriodSeconds: 30
      volumes:
      - name: varlog
        hostPath:
          path: /var/log
      - name: varlibdockercontainers
        hostPath:
          path: /var/lib/docker/containers
```

- `kubectl apply -f fluentd-elasticsearch.yaml`

# hogehoge という namespace に pod を配置しなさい

```
apiVersion: v1
kind: Pod
metadata: 
  name: busybox-sleep
spec: 
  containers: 
  - name: busybox
    image: busybox
    args:
    - sleep
    - "10000"
```

- `kubectl apply -f --namespace=hogehoge`

# pod が出力している log をファイルに書き出しなさい

# test_deploy という deployment を scale させて replica の数を 5 にしなさい

# nginx:1.11 の image を使用して sample_nginx という deployment を作成後、image を nginx:1.12 に更新し、rollback させなさい

# PersistentVolume の一覧を capacity で sort して結果をファイルに書き出しなさい

- `kubectl get pvc xxx -o json`
- ソートしたいjsonのパスを調べる
  - 今回の場合、 `status.canpacity.storage` (items配下からパスを探してくれる)
- `kubectl get pvc --sort-by=status.capacity.storage`
- ヘッダを書くか、とかファイルの形式は問題をちゃんと確認すること
- `kubectl get pvc -o jsonpath='{.items[*].metadata.name}` とかすると名前が取れる

# service を NodePort で作成し、pod にアクセスできるようにしなさい

# etcd の snapshot を作成しなさい

# CPU 使用率が一番高い pod 名をファイルに書き出しなさい

- `kubectl top pod`
- 上記でpodのCPU占有時間が出てくるので、それで判断

# hoge_node という node をスケジュールから外し、pod を再配置しなさい(強制的に)

# test_service という service でアクセスできる pod を全てファイルに書き出しなさい

- `kubectl descrive svc`
- サービスのセレクタを確認
- `kubectl get po -l label=value`
- `kubectl get po -L ${label_name}`
  - `-L` オプションは出力カラムの追加
- `kubectl get po --show-labels`
- ラベル全部表示

# pod が自動的に起動するようにしなさい (static pod)

> https://kubernetes.io/docs/tasks/administer-cluster/static-pod/

1. yaml配置用のdirectoryをほる
2. KUBELET_ARGSにstatic pod用のyamlを配置するためのディレクトリを示す `--pod-manifest-path` オプションを追加する
  - kubeletに設定するので、node毎にできるので、daemonsetっぽい使い方もできる
3. kubelet 再起動 (daemon-reload と restart)
4. staric pod用のyamlを作成して任意の場所におく

# cluster の node を master に登録しなさい

- kubeletが上がってないだけの問題
- CKAの問題としてはsystemctl startで起動してあげれば動くはず
- systemctl enableも忘れずに
- ただし、tokenの認証をbootstrap xxx を使ってやらないといけないケースは8%問題

# PersistentVolume を hostPath で作成しなさい

# Deployment および Service を作成後、nslookup を使って名前を解決し、ファイルに書き出しなさい

# pod の起動に失敗しているので、InitContainer を使って失敗を回避しなさい

# nginx と redis と memcached が含まれた pod を作成しなさい

# Ready 状態の node の数をファイルに書き出しなさい (1%)

- `kubectl get nodes`
- masterは計算に含めるかどうかを問題文をよく読むことが必要
- この問題形式の場合、masterはREADY状態でない可能性が高い
