# PLAS TESK

In this repository, you can find the instructions to install PLAS-TESK, an extension of the original [TESK](https://github.com/elixir-cloud-aai/TESK).

PLAS-TESK is an element of the [PLAS project](https://github.com/PlatformedTasks/Documentation) funded by the [GÉANT Innovation Programme](https://community.geant.org/community-programme-portfolio/innovation-programme/) initiative to extend the [GÉANT Cloud Flow (GCF)](https://clouds.geant.org/community-cloud/) to be capable of performing platformed-tasks in the cloud.


![PLAS extension](src/tesk-plas.png)

## Requirements
1. A Kubernetes cluster with version >= v1.21 installed
2. [Helm](https://helm.sh/docs/intro/install/) version >= 3 installed
3. NFS provisioner, follow the steps from the [PLAS Documentation](https://github.com/PlatformedTasks/Documentation/blob/main/configure_plas_testbed.md)
4. FTP server installed 
   
## Quickstart
1. Clone this repository and change directory

```console
$ git clone https://github.com/PlatformedTasks/PLAS-TESK.git
$ cd PLAS-TESK/charts/tesk/
```

2. Since we are going to install PLAS-TESK as a Helm chart, edit the `values.yaml` file to match your configurations. 
From the original [TESK chart](https://github.com/elixir-cloud-aai/TESK) we have added the option `storage: mystorage` which will deploy an NFS provisioner to the Kubernetes cluster called `example.com/nfs`.
3. Create a `secrets.yaml`  file with the FTP credentials:

```yaml
ftp:
  username: <username>
  password: <password>
```

4. Finally, install the PLAS-TESK-API using Helm:

```console
helm install plas-tesk-api . -f secrets.yaml -f values.yaml
```