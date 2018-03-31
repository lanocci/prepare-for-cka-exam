# Basic

- `kubectl autoscale -f ${MANIFEST FILE NAME} --max=${MAX POD COUNT}`
- `kubectl autoscale ${RESOURCE TYPE}/${RESOURCE NAME} --max=${MAX POD COUNT}`
- `kubectl autoscale ${RESOURCE TYPE} ${RESOURCE NAME} --max=${MAX POD COUNT}`

# Options

- `--min=${MIN POD COUNT}`
- `--cpu-percent=${CPU USAGE IN PERCENT}`

> https://kubernetes-v1-4.github.io/docs/user-guide/kubectl/kubectl_autoscale/
