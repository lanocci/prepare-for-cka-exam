# Overview

## 用途・種類別コマンド一覧

> https://kubernetes.io/docs/reference/kubectl/cheatsheet/

### kubeconfig系

- [kubectl config](./config.md)

### リソース確認

- 一覧表示
  - [kubectl get](./get.md)
- 詳細表示
  - [kubectl describe](./describe.md)

### リソース編集

- manifestファイルを適用
  - [kubectl apply](./apply.md)
- 動いてるmanifestを修正
  - [kubectl edit](./edit.md)
- 動いてるcomputeリソースの設定変更
  - [kubectl set](./set.md)

### Node

- ノードからPodを退避
  - [kubectl drain](./drain.md)
- Nodeをスケジュール対象から外す
  - [kubectl cordon](./cordon.md)

### Replication Controller / Job / Deployment

- スケールアウト・スケールイン
  - [kubectl scale](./scale.md)

### Replica Set / Deployment

- オートスケール
  - [kubectl autoscale](./autoscale.md)

### Deployment

- 履歴
  - [kubectl rollout](./rollout.md)

### コンテナ

- コンテナのログを確認
  - [kubectl log](./log.md)

### [Global Options](./global-options.md)
