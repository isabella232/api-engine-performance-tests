# Varnish API Engine 2.0 performance test deployment

This is the [Ansible](https://docs.ansible.com/ansible/) configuration used to prepare a Varnish API Engine 2.0 environment on CentOS 7 for performance tests.

## Requirements

Required pre configured repositories:

* Varnish Plus 4
* API Engine

Required firewall openings:

* Consumers -> Backends: ``1337/tcp``
* Consumers -> Varnish: ``6081/tcp``
* Management -> Statistics: ``6555/tcp``
* Varnish -> Accounting: ``11211/tcp``
* Varnish -> Backends: ``1337/tcp``
* Varnish -> Management: ``8080/tcp``
* Varnish -> Statistics: ``5558/tcp``

## Setup

1. Prepare 12 instances running CentOS 7.
2. Add the required repositories manually (see Requirements).
3. Ensure firewall openings are in place (see Requirements).
4. Add the IP addresses of the instances to the Ansible ``inventory`` file.
5. Deploy the configuration using ``run-ansible``.
6. The test scripts are available in ``/usr/local/bin/`` on the consumer instances.

## Sources

* Boom is pre-built with a couple of patches to get support for keep-alive and custom host header. The sources are available at https://github.com/espebra/boom/.
* Dummy-api is pre-built. The sources are available at https://github.com/espebra/dummy-api/.

## Considerations

This configuration is not using TLS/SSL.
