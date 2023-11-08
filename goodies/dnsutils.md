## DNS Utils 

DNSUtils is a small container which you can use to check DNS resolution inside a Kubernetes cluster.

Creating the container can be done by executing the following example, which applies the Pod Kubernetes manifest:

```shell
cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: Pod
metadata:
  name: dnsutils
  namespace: default
spec:
  containers:
  - name: dnsutils
    image: gcr.io/kubernetes-e2e-test-images/dnsutils:latest
    command:
      - sleep
      - "3600"
    imagePullPolicy: IfNotPresent
  restartPolicy: Always
EOF
```

Once the Pod has been created, you can test DNS resolution by executing the `dig` command inside the container:

```shell
kubectl exec dnsutils -it -- dig google.com
```