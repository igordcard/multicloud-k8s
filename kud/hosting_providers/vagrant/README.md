# Kubernetes Deployment

## Summary

This project offers a means for deploying a Kubernetes cluster
that satisfies the requirements of [ONAP multicloud/k8s plugin][1]. Its
ansible playbooks allow provisioning a deployment on Virtual Machines.

![Diagram](../../../docs/img/diagram.png)

## Deployment

The [installer](installer.sh) bash script contains the minimal
Ubuntu instructions required for running this project.

### Virtual Machines

This project uses [Vagrant tool][2] for provisioning Virtual Machines
automatically. The [setup](setup.sh) bash script contains the
Linux instructions to install dependencies and plugins required for
its usage. This script supports two Virtualization technologies
(Libvirt and VirtualBox).

    $ sudo ./setup.sh -p libvirt

There is a `default.yml` in the `./config` directory which creates multiple controllers and nodes.
There are also sample configurations in the `./config/samples` directory.  To use one of the samples,
copy it into the `./config` directory as `pdf.yml`.  If a `pdf.yml` exists in the `./config`
directory it overrides the `default.yml` when the `vagrant up` command (in the next step) is run.
For example:

    $ cp ./config/samples/pdf.yml.aio ./config/pdf.yml

Once Vagrant is installed, it's possible to provision a cluster using
the following instructions:

    $ vagrant up && vagrant up installer

In-depth documentation and use cases of various Vagrant commands [Vagrant commands][3]
is available on the Vagrant site.

## License

Apache-2.0

[1]: https://git.onap.org/multicloud/k8s

[2]: https://www.vagrantup.com/

[3]: https://www.vagrantup.com/docs/cli/
