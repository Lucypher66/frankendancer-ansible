# Frankendancer Ansible Boilerplate

This repository provisions a single-host Frankendancer full node plus a production-facing HTTPS RPC endpoint.

## Why the host looks like this

The host is designed as self-explaining as possible. Drives are mounted at /mnt/. That seems counter-intuitive, since a non-root user needs to access it, but /mnt is the standard mountpoint for additional drives and it is no home directory of any user. The git repo lives default at /opt/, since /opt/ is usually the place where optional applications are stored. Binaries are linked to /bin, since they are executable binaries, etc. 

The goal was to have a system that is ready to "fire and forget". Run ansible, wait for it to finish, sync up and be happy. This is why anything is created by ansible and steered through variables. You can copy the playbook and also have a configuration ready for the host to push into a git repo to restore the host in case of a disaster. No manual editing of a file, just ansible. 

## Repository structure

The goal of this ansible playbook is to be as dynamic as possible. And so is this repo nothing more than a simple ansible playbook. No extra files to be shipped apart from resources i've referenced, which could be omitted afterwards. No overhead that could make problems. This playbook is designed to ship anything in one file. Including file contents. Anything relevant is steered through variables.

## How non-automatable work is handled

The only thing needed to be done is to install ansible-core.
This is done using the following command:

```bash
sudo apt update
sudo apt install -y ansible-core
```


## Quick start

Clone the repository and run the following as root or a sudo-enabled user:
```bash
sudo ansible-playbook install-frankendancer.yml
```

## Notes

- This playbook assumes root-level host provisioning and will partition and format the configured storage devices.
- Validate device mappings before first run to avoid destructive disk mistakes.
