

## Deploying the Dashboard UI

The Dashboard UI is not deployed by default. To deploy it, run the following command:

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.5.0/aio/deploy/recommended.yaml
```

## Accessing the Dashboard UI

To protect your cluster data, Dashboard deploys with a minimal RBAC configuration by default.
Currently, Dashboard only supports logging in with a Bearer Token.
To create a token for this demo, you can follow our guide on
[creating a sample user](https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md).

{{< warning >}}
The sample user created in the tutorial will have administrative privileges and is for educational purposes only.
{{< /warning >}}

### Command line proxy

You can enable access to the Dashboard using the `kubectl` command-line tool,
by running the following command:

```
kubectl proxy
```

Kubectl will make Dashboard available at [http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/](http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/).

The UI can _only_ be accessed from the machine where the command is executed. See `kubectl proxy --help` for more options.

{{< note >}}
The kubeconfig authentication method does **not** support external identity providers
or X.509 certificate-based authentication.
{{< /note >}}
