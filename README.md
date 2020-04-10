# terraform-render-bootkube

## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.12 |
| local | ~> 1.2 |
| template | ~> 2.1 |
| tls | ~> 2.0 |

## Providers

| Name | Version |
|------|---------|
| local | ~> 1.2 |
| template | ~> 2.1 |
| tls | ~> 2.0 |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| api\_servers | List of domain names used to reach kube-apiserver from within the cluster | `list(string)` | n/a | yes |
| api\_servers\_external | List of domain names used to reach kube-apiserver from an external network | `list(string)` | `[]` | no |
| api\_servers\_ips | List of additional IPv4 addresses to be included in the kube-apiserver TLS certificate | `list(string)` | `[]` | no |
| asset\_dir | Path to a directory where generated assets should be placed (contains secrets) | `string` | n/a | yes |
| certs\_validity\_period\_hours | Validity of all the certificates in hours | `number` | `8760` | no |
| cloud\_provider | The provider for cloud services (empty string for no provider) | `string` | `""` | no |
| cluster\_domain\_suffix | Queries for domains with the suffix will be answered by kube-dns | `string` | `"cluster.local"` | no |
| cluster\_name | Cluster name | `string` | n/a | yes |
| container\_arch | Architecture suffix for the container image coredns/coredns:coredns- (e.g., arm64) | `string` | `"amd64"` | no |
| container\_images | Container images to use (the coredns entry will get -${var.container\_arch} appended) | `map(string)` | <pre>{<br>  "calico": "calico/node:v3.13.1",<br>  "calico_cni": "calico/cni:v3.13.1",<br>  "coredns": "coredns/coredns:coredns-",<br>  "hyperkube": "k8s.gcr.io/hyperkube:v1.18.0",<br>  "kube_apiserver": "k8s.gcr.io/kube-apiserver:v1.18.0",<br>  "kube_controller_manager": "k8s.gcr.io/kube-controller-manager:v1.18.0",<br>  "kube_proxy": "k8s.gcr.io/kube-proxy:v1.17.4",<br>  "kube_scheduler": "k8s.gcr.io/kube-scheduler:v1.18.0",<br>  "pod_checkpointer": "kinvolk/pod-checkpointer:83e25e5968391b9eb342042c435d1b3eeddb2be1"<br>}</pre> | no |
| enable\_aggregation | Enable the Kubernetes Aggregation Layer (defaults to false, recommended) | `bool` | `false` | no |
| enable\_reporting | Enable usage or analytics reporting to upstream component owners (Tigera: Calico) | `bool` | `false` | no |
| etcd\_servers | List of domain names used to reach etcd servers. | `list(string)` | n/a | yes |
| expose\_on\_all\_interfaces | If true, kube-apiserver will be exposed on all controller node interfaces on port 6443. If false, it will be exposed only one kubelet's node IP. | `bool` | `false` | no |
| external\_apiserver\_port | External kube-apiserver port (e.g. 6443 to match internal kube-apiserver port) | `number` | `6443` | no |
| network\_encapsulation | Network encapsulation mode either ipip or vxlan (only applies to calico) | `string` | `"ipip"` | no |
| network\_ip\_autodetection\_method | Method to autodetect the host IPv4 address (only applies to calico) | `string` | `"first-found"` | no |
| network\_mtu | CNI interface MTU | `number` | `1500` | no |
| pod\_cidr | CIDR IP range to assign Kubernetes pods | `string` | `"10.2.0.0/16"` | no |
| service\_cidr | CIDR IP range to assign Kubernetes services.<br>The 1st IP will be reserved for kube\_apiserver, the 10th IP will be reserved for kube-dns. | `string` | `"10.3.0.0/24"` | no |
| trusted\_certs\_dir | Path to the directory on cluster nodes where trust TLS certs are kept | `string` | `"/usr/share/ca-certificates"` | no |

## Outputs

| Name | Description |
|------|-------------|
| ca\_cert | n/a |
| calico\_values | n/a |
| cluster\_dns\_service\_ip | n/a |
| etcd\_ca\_cert | n/a |
| etcd\_client\_cert | n/a |
| etcd\_client\_key | n/a |
| etcd\_peer\_cert | n/a |
| etcd\_peer\_key | n/a |
| etcd\_server\_cert | n/a |
| etcd\_server\_key | n/a |
| kube-apiserver\_values | n/a |
| kubeconfig-admin | Generated kubeconfig for admins (i.e. human super-user) |
| kubeconfig-kubelet | Generated kubeconfig for Kubelets (i.e. lower privilege than admin) |
| kubelet\_cert | n/a |
| kubelet\_key | n/a |
| kubelet\_values | n/a |
| kubernetes\_values | n/a |
| pod-checkpointer\_values | values.yaml content for all deployed charts. |
| server | n/a |
| server\_admin | n/a |

