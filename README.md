# Grommunio Deployment on K8s 

This is the project prototype for running Grommunio on k8s


## Setup Instructions 

* Ensure that you have a running k8s cluster. 
  * You can test with single-node clusters like [minikube](https://minikube.sigs.k8s.io/docs/start/) or [KIND](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)
  * For testing, we use KIND

* Enable ipv6 kernel module
  * Edit /etc/docker/daemon.json, set the ipv6 key to true and the fixed-cidr-v6 key to your IPv6 subnet. In this example we are setting it to 2001:db8:1::/64.
```
{
  "ipv6": true,
  "fixed-cidr-v6": "2001:db8:1::/64"
}
```
  * Reload the Docker configuration file.

```
systemctl reload docker
```

* Don't forget to change hostname to suit your needs

* Get a certificate for your chosen domain and place both the secret and public keys in the `./tls_keys` folder.
  * A self-signed certificate can be generated for testing purposes (use a wildcard certificate that uses the FQDN of the hostname above):
  ```
  openssl req -x509 -nodes -newkey rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365 -subj '/CN=*.testing.com'
  ```

## Getting started

* Check the README in the k8s_files directory. 
