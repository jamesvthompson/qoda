## Install Kubectl

kubectl is installable on a variety of Linux platforms, macOS and Windows. Find your preferred operating system below.

[Install kubectl on Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux)

[Install kubectl on macOS](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos)

[Install kubectl on Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows)

## Install Run:ai CLI 


### "Mac or Linux"

Go to the Run:ai user interface. On the top right select `Researcher Command Line Interface`.

<img width="1474" alt="1 Screen Shot 2023-03-01 at 11 40 57 AM" src="https://user-images.githubusercontent.com/109220448/222215643-0bb73783-c673-429c-bc70-4d1a641f3a4e.png">

Select `Mac` or `Linux`. 

<img width="1265" alt="Screen Shot 2023-03-01 at 11 41 44 AM" src="https://user-images.githubusercontent.com/109220448/222215765-990cc9dd-b3d2-4237-882c-fc8c74e84945.png">

Copy the command and run it on a remote machine and run the following.

<img width="1281" alt="Screen Shot 2023-03-01 at 11 41 26 AM" src="https://user-images.githubusercontent.com/109220448/222215935-00d9ea97-7470-4057-81b9-cbff2f2c2c40.png">

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

### Kubernetes Ruin:AI CLI Configuration

Copy the provided Run:AI Kubernetes configuration file into your working directory. 

```
export KUBECONFIG=<Kubernetes-config-file>
```
Lets login to your user
```
runai login
```
Configure your project 
```
runai config project <your project>
```
Then we can list the running jobs we have
```
runai list jobs
```
It should look similar to the image below,
![Screen Shot 2023-03-01 at 12 28 01 PM](https://user-images.githubusercontent.com/109220448/222217802-d6cf3275-05de-4f75-b592-53a36247e88e.png)

### Submit and Connect to qoda

Now we can submit the job via the command line interface with the following comands 

```
runai submit -i robmagno/qoda:latest -g 1 --interactive
```
![Screen Shot 2023-03-01 at 12 47 56 PM](https://user-images.githubusercontent.com/109220448/222220768-b2bb0275-e76c-47ac-829b-513284a29d49.png)

Now check if the job is running this may take a few minutes
```
runai list jobs
```
![Screen Shot 2023-03-01 at 12 49 12 PM](https://user-images.githubusercontent.com/109220448/222221023-ed3f91bd-42b5-4769-95b3-d299a0d01d3b.png)

Now we can copy the running job name with the qoda image and bash into it

```
runai bash <job name>
```
![Screen Shot 2023-03-01 at 12 51 18 PM](https://user-images.githubusercontent.com/109220448/222221515-d0653171-c3f2-41ee-9cba-e1cb99ec4159.png)

To exit the session you can use ctrl d to detach

Now to stop the job you can run
```
runai delete job <job name>
```
![Screen Shot 2023-03-01 at 12 51 27 PM](https://user-images.githubusercontent.com/109220448/222221985-66f7ef2c-cd4f-4e89-ae69-1b437e6729b8.png)
