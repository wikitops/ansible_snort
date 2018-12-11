# Ansible : Playbook Snort

The aim of this project is to deploy Snort on Linux Vagrant instance.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

What things you need to run this Ansible playbook :

*   [Vagrant](https://www.vagrantup.com/docs/installation/) must be installed on your computer
*   Update the Vagrant file based on your computer (CPU, memory), if needed
*   Update the operating system to deploy in the Vagrant file (default: Ubuntu)
*   Download the Ansible requirements:

```bash
$ ansible-galaxy install -r requirements.yml
```

### Usage

A good point with Vagrant is that you can create, update and destroy all architecture easily with some commands.

Be aware that you need to be in the Vagrant directory to be able to run the commands.

#### Deployment

To deploy Snort on Vagrant instances, just run this command :

```bash
$ vagrant up
```

If everything run as expected, you should be able to list the virtual machine created :

```bash
$ vagrant status

Current machine states:

snort01                   running (virtualbox)
```

If everything run has expected, you should have Snort up and running on the Vagrant instance.

```bash
$ sudo snort -T -c /etc/snort/snort.conf

[...]

Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 3.0  <Build 1>
Preprocessor Object: SF_SSH  Version 1.1  <Build 3>
Preprocessor Object: SF_FTPTELNET  Version 1.2  <Build 13>
Preprocessor Object: SF_SMTP  Version 1.1  <Build 9>
Preprocessor Object: SF_DNP3  Version 1.1  <Build 1>
Preprocessor Object: SF_GTP  Version 1.1  <Build 1>
Preprocessor Object: SF_SSLPP  Version 1.1  <Build 4>
Preprocessor Object: SF_REPUTATION  Version 1.1  <Build 1>
Preprocessor Object: SF_MODBUS  Version 1.1  <Build 1>
Preprocessor Object: SF_SDF  Version 1.1  <Build 1>
Preprocessor Object: SF_SIP  Version 1.1  <Build 1>
Preprocessor Object: SF_DCERPC2  Version 1.0  <Build 3>
Preprocessor Object: SF_IMAP  Version 1.0  <Build 1>
Preprocessor Object: SF_DNS  Version 1.1  <Build 4>
Preprocessor Object: SF_POP  Version 1.0  <Build 1>
Preprocessor Object: appid  Version 1.1  <Build 5>

Snort successfully validated the configuration!
Snort exiting
```

#### Destroy

To destroy the Vagrant resources created, just run this command :

```bash
$ vagrant destroy
```

### How-To

This section list some simple command to use and manage the playbook and the Vagrant hosts.

#### Update with Ansible

To update the Snort configuration with Ansible, you just have to run the Ansible playbook snort.yml with this command :

```bash
$ ansible-playbook snort.yml
```

#### Update with Vagrant

To update the Snort configuration with Vagrant, you just have to run provisioning part of the Vagrant file :

```bash
$ vagrant provision
```

#### Connect to Vagrant instance

To be able to connect to a Vagrant instance, you should use the CLI which is configured to automatically use the default SSH key :

```bash
$ vagrant ssh snort01
```

## Author

Member of Wikitops : https://www.wikitops.io/

## Licence

This project is licensed under the Apache License, Version 2.0. For the full text of the license, see the LICENSE file.
