If you’re using kube-proxy in IPVS mode, since Kubernetes v1.14.2 you have to enable strict ARP mode.
#kubectl edit configmap -n kube-system kube-proxy
-------------
apiVersion: kubeproxy.config.k8s.io/v1alpha1
kind: KubeProxyConfiguration
mode: "ipvs"
ipvs:
  strictARP: true
-------------
#helm repo add metallb https://metallb.github.io/metallb
#helm install metallb metallb/metallb

Post installing the metallb on the cluster we will need to configure the ipAddressAllocation by applying the yaml in metallb directory along with the application of the L2Advertisement.

#kubectl create -f ipaddressallocation.yaml
#kubectl create -f L2Advertisement.yaml.

This will create a metallb controller and speaker on your cluster.