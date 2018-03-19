# Basic

- `kubectl scale --replicas=${COUNT} -f ${MANIFEST FILE NAME}`
- `kubectl scale --replicas=${COUNT} ${RESOURCE TYPE}/${RESOURCE NAME} ...`
  - ex.) `kubectl scale --replicas=3 deployment/test-deployment`
  - リソースを複数指定することも可能

# Options 

- `--current-replicas=${COUNT}`
  - 「現在のレプリカ数が${COUNT}だったら」という条件の指定
- `--resource-version=${VERSION}`
  - 「現在のリソースのバージョンがいくつだったら」という条件の指定
