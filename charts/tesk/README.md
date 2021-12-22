# Instruction to deploy PLAS TESK

This directory contains the chart file to deploy the PLAS extension of TESK service. Tested with Helm v3.6.3.

For more information see the [README](https://github.com/elixir-cloud-aai/TESK/blob/master/charts/tesk/README.md) on the original TESK

## Deployment

Since this is a helm chart, you must check that you have Helm installed.

To deploy the application:
* Edit the [`values.yaml`](values.yaml) according to your configuration.
* For the storage you can choose between three options:
  1. **openstack** 
  2. **s3:** to use s3 storage add the necessary `config` and `credentials` files to the **s3-config** (*charts/tesk/s3-config*) folder.
  3. **mystorage:** if you decide to use a custom storage class with an FTP storage backend, you need to create a `secrets.yaml` file with the  `username` and `password` of the ftp account
```
 ftp:
   username: <username>
   password: <password>
 ```
 

 * Execute the command:

```bash
$ helm upgrade --install tesk-release . -f secrets.yaml -f values.yaml 
```

and check if everything went well:

```bash
$ helm list -n tesk
NAME	        NAMESPACE  REVISION	UPDATED                                 	STATUS  	CHART     	APP VERSION
tesk-release	default	     1      	2021-12-20 13:24:34.08857551 +0100 CET	deployed	tesk-0.1.0	dev
```
