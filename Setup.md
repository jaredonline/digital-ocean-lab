# Digital Ocean Kubernetes Lab Setup
Documenting how I set this mad world up

## Setup

### Overview
[This article](http://5pi.de/2016/11/20/15-producation-grade-kubernetes-cluster/)
came up when doing some Google'ing and was the basis for a lot of my decisions.

 - Host on Digital Ocean
 - Use Terraform for hosting

### Terraform
Other places are using [Terraform](https://www.terraform.io/downloads.html). I
will do so as well, why not.

### Hosting
Digital Ocean 'cause its cheap and offers non-US locations.
[This article](https://thehftguy.com/2016/06/08/choosing-a-cloud-provider-amazon-aws-ec2-vs-google-compute-engine-vs-microsoft-azure-vs-ibm-softlayer-vs-linode-vs-digitalocean-vs-ovh-vs-hertzner/)
came up first when I Googled `amazon vs google vs digitalocean`

### Packer
[Packer](https://www.packer.io) is used to create the machine images that get 
deployed.

I spent an ungodly amount of time trying to understand the relationship between
Packer and Terraform. I tried to make a dummy image with Packer and it wasn't
working (the docs aren't great). I kept seeing that it was making a droplet as
the first step and failing because it couldn't connect to SSH. I assumed it
was not just creating the image but creating the droplet too. It turns out it
needs to create the droplet, run the installs, then create the image. Then I
use the image ID in Terraform to launch the actual droplets.

### OS
Probably CoreOS, using [these docs](https://coreos.com/kubernetes/docs/latest/)

## Monitoring

TBD, Prometheus, StatsD, Grafana

## Logging

TBD, [Splunk free](https://www.splunk.com/en_us/products/splunk-enterprise/free-vs-enterprise.html)?
[ELK](https://www.elastic.co/webinars/introduction-elk-stack)?

# Todo
 
 - Figure out certs
 - Figure out Digital Ocean setup
