# コマンドのスコープに関連するもの
      
- `--namespace=""`
  - コマンドの対象とするnamespaceを指定

# SSL/TLS通信に関連するもの

- --certificate-authority="": Path to a cert. file for the certificate authority.
- --client-certificate="": Path to a client certificate file for TLS.
- --client-key="": Path to a client key file for TLS.
- `--insecure-skip-tls-verify`
  - default: [=false]
  - If true, the server's certificate will not be checked for validity. This will make your HTTPS connections insecure.

# クラスタ/ APIサーバへの通信・認証に関連するもの

- --cluster="": The name of the kubeconfig cluster to use
- --context="": The name of the kubeconfig context to use
- --kubeconfig="": Path to the kubeconfig file to use for CLI requests.
- --password="": Password for basic authentication to the API server.
- -s, --server="": The address and port of the Kubernetes API server
- --token="": Bearer token for authentication to the API server.
- --user="": The name of the kubeconfig user to use
- --username="": Username for basic authentication to the API server.

# ログ出力に関連するもの
- --alsologtostderr[=false]: log to standard error as well as files
- --log-backtrace-at=:0: when logging hits line file:N, emit a stack trace
- --log-dir="": If non-empty, write log files in this directory
- --log-flush-frequency=5s: Maximum number of seconds between log flushes
- --logtostderr[=true]: log to standard error instead of files
- --stderrthreshold=2: logs at or above this threshold go to stderr
- --v=0: log level for V logs
- --vmodule=: comma-separated list of pattern=N settings for file-filtered logging

# kubernetesのバージョン指定

--match-server-version[=false]: Require server version to match client version
