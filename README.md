# daemonset-job [WIP]

Kubernetes Operator for creating Jobs backed by Daemonsets.

Following is an example for a cleanup job using a container with entrypoint
`rm -rf`. Filepath argument and mount path can be passed as part of the custom
resource Job.

```yaml
apiVersion: daemonset.darkowlzz.space/v1beta1
kind: Job
metadata:
  name: job-sample
spec:
  image: darkowlzz/cleanup:v0.0.2
  args: ["/basetarget/foo"]
  mountPath: "/tmp"
```

When deployed, this would execute `rm -rf /tmp/foo` on all the nodes.
