# Using VPN to Access Kontena Platform

> Prerequisites: OpenVPN client installed to your computer.

All Kontena Services run inside a virtual private network (VPN) by default. Therefore, none of the Kontena Services are exposed to the Internet unless explicitly defined to be exposed. The benefits of this approach are obvious; most of the modern micro-service architectures expose only the frontend of the application to the Internet while keeping internal services such as databases sealed off from any unauthorized access. The frontend application may access the database since both of these components belong to the same VPN. This is great architecture, but it poses some challenges when the entire platform is based on containers.

Developers and DevOps teams will require access to all internal services for tasks such as making database backups. It is also beneficial for them to be able to use the existing standard tools for these maintenance operations. With Kontena, this is possible using the built-in VPN access to the virtual private network where all services are running.

You should use the Kontena's built-in VPN access if you want to:

* Create your application with a micro-service architecture and expose only the front-end part of your application to the Internet.
* Use [Kontena Image Registry](./image-registry.md) for storing your own application container images.
* Focus on developing your application instead of tooling around it.

In this chapter, we'll discover how to use VPN to access Kontena Platform:

* [Create VPN Service](#create-vpn-service)
* [Export VPN Configuration](#export-vpn-configuration)
* [Delete VPN Service](#delete-vpn-service)

## Create VPN Service

> NOTE! The VPN service uses port 1194 (UDP). Remember to open this port to Kontena Nodes if you are using a firewall!

```
$ kontena vpn create
Usage:
    kontena vpn create [OPTIONS]

Options:
    --node NODE                   Node name where VPN is deployed
    --ip IP                       Node ip-address to use in VPN service configuration
```

Use the `--node` and/or `--ip` option to override automatic Node selection and IP detection in private network setups.

## Export VPN Configuration

```
$ kontena vpn config > /path/to/kontena.ovpn
```

The `kontena.ovpn` configuration file can be then imported to your favorite OpenVPN client.

## Delete VPN Service

```
$ kontena vpn remove
```
