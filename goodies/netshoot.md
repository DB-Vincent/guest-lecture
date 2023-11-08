# Netshoot

DNSUtils is a small container which you can use to troubleshoot network issues inside a Kubernetes cluster.

Creating the container can be done by executing the following example, which applies the Pod Kubernetes manifest:

```shell
cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: Pod
metadata:
  name: netshoot
  namespace: default
spec:
  containers:
  - name: netshoot
    image: nicolaka/netshoot:latest
    command:
      - sleep
      - "3600"
    imagePullPolicy: IfNotPresent
  restartPolicy: Always
EOF
```

Once the Pod has been created, you can access the shell inside the container by executing the following command:

```shell
kubectl exec netshoot -it -- /bin/sh
```

Inside of the container you have access to a whole list of tools which you can use to troubleshoot network issues:
- apache2-utils
- bash
- bind-tools
- bird
- bridge-utils
- busybox-extras
- conntrack-tools
- curl
- dhcping
- drill
- ethtool
- file
- fping
- grpcurl
- iftop
- iperf
- iperf3
- iproute2
- ipset
- iptables
- iptraf-ng
- iputils
- ipvsadm
- jq
- libc6-compat
- liboping
- ltrace
- mtr
- net-snmp-tools
- netcat-openbsd
- nftables
- ngrep
- nmap
- nmap-nping
- nmap-scripts
- openssl
- py3-pip
- py3-setuptools
- scapy
- socat
- speedtest-cli
- openssh
- strace
- tcpdump
- tcptraceroute
- tshark
- util-linux
- vim
- git
- zsh
- websocat
- swaks
- perl-crypt-ssleay
- perl-net-ssleay