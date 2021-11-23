+Netwrok polices
+ClusterRole bindings
+PodSecurityPolicy 

Best practices of Dockerfile and Manifest
+AuditLog
+CLusterRole bindings

Fix Config files in /etc/kubernetes/manifests (https://v1-18.docs.kubernetes.io/docs/reference/command-line-tools-reference/)
- etcd
- api-server
- Kublet (Where is Kublet configuration file ?)

-Question: Allow all traffic for Ingress + Egress.
+Question: Using Admission Controllers and Plugins 
+Question: Security Context https://kubernetes.io/docs/tasks/configure-pod-container/security-context/
+Question: Using secrets by pod (echo "" base64 -d)
Question: Auditing https://kubernetes.io/docs/tasks/debug-application-cluster/audit/
Question: RBAC https://kubernetes.io/docs/reference/access-authn-authz/rbac/
+Question: Runtime class https://kubernetes.io/docs/concepts/containers/runtime-class/

privileged Pods.
App Armor

apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: prevent-psp-policy
spec:
  privileged: false
  seLinux:
    rule: RunAsAny
  supplementalGroups:
    rule: RunAsAny
  runAsUser:
    rule: RunAsAny
  fsGroup:
    rule: RunAsAny
  volumes:
  - '*'

Question: Create a new ClusterRole named restrict-access-role, which uses the newly created PodSecurityPolicy prevent-psp-policy

Question: Inspect Pods running in namespace production and delete any Pod that is either not stateless or not immutable.

Question: Create a NetworkPolicy named pod-access to restrict access to Pod users-service running in namespace dev-team and selector xxx.
Only allow the following Pods to connect to Pod users-service:
  - Pods in the namespace qa 
  - Pods with label environment: testing, in any namespace

Question: Trivy The container image scanner shall scan for and reject the use of vulnerable images.
List pod images:
- amazonlinux:1
- alpine:3.12

+Question: Enforce the prepared AppArmor profile located at /etc/apparmor.d/nginx_apparmor.
+Question: analyse the container's behaviour for at least 30 seconds, using filters that detect newly spawning and executing processes.
- sysdig
- falco

-Question: Store an incident file at /opt/KSRS00101/incidents/details, containing the detected incidents, one per line, in the following format:
[xxx][yyy][zzz]
