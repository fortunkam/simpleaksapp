# Simple AKS App

This will deploy a simple 2 part AKS App containing
- An AspNetCore MVC app
- An AspNetCore API app
- An Internal Loadbalancer

The application is designed to be run on private clusters with the MVC app exposed through a vnet internal address.
The MVC app calls the API over the AKS internal network (not external to the cluster)
