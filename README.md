### Install Kubectl

kubectl is installable on a variety of Linux platforms, macOS and Windows. Find your preferred operating system below.

[Install kubectl on Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux)

[Install kubectl on macOS](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos)

[Install kubectl on Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows)


### Kubernetes Configuration

On the Researcher's root folder, create a directory _.kube_. Copy the Kubernetes configuration file into the directory. Each Researcher should have a __separate copy__ of the configuration file. The Researcher should have _write_ access to the configuration file as it stores user defaults. 
If you choose to locate the file at a different location than `~/.kube/config`, you must create a shell variable to point to the configuration file as follows:

```
export KUBECONFIG=<Kubernetes-config-file>
```

Test the connection by running:

```
kubectl get nodes
```

### Install Run:ai CLI 


### "Mac or Linux"

Go to the Run:ai user interface. On the top right select `Researcher Command Line Interface`.

Select `Mac` or `Linux`. 

Download directly using the button or copy the command and run it on a remote machine and run the following.

``` 
chmod +x runai
sudo mv runai /usr/local/bin/runai
```


### "Windows" 

Install [Docker for Windows](https://docs.docker.com/docker-for-windows/install/){target=_blank}.

Get the following folder from GitHub: [https://github.com/run-ai/docs/tree/master/cli/windows](https://github.com/run-ai/docs/tree/master/cli/windows){target=_blank}.

Replace `config` with your Kubernetes Configuration file.

Replace `<CLUSTER-URL>` in the Dockerfile with the URL of the cluster. The URL can be found in the `Clusters` view of the Run:ai user interface. 

Run: `build.sh` to create a docker image named `runai-cli`.

Test the image by running:

``` 
docker run -it runai-cli bash
```

Try and connect to your cluster from inside the docker by running a Run:ai CLI command. E.g. `runai list projects`.

Distribute the image to Windows users.


In case you want to use port-forward feature please use the following command

``` 
docker run -it -p <PORT>:<PORT> runai-cli bash
```

And when using `runai submit` command add the following flag:

```
--address 0.0.0.0
```

