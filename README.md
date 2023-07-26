![BlackMega-VM_Logo](https://github.com/r0ttenbeef/BlackMega-VM/assets/48027449/554012a0-685b-4739-9ba7-fc1e33e772fd)
<div align="center">

![Ansible Win](https://img.shields.io/badge/Ansible-Windows-black.svg)
![OS Windows](https://img.shields.io/badge/Supported%20OS-Windows11-blue.svg)

</div>
---
# BlackMega-VM
Convert windows virtual machine to a lab for malware analysis using ansible playbooks for automated installation of malware analysis tools and gadgets, Debloating useless windows services to reduce windows traffic noise and overwhelming running processes.

## Wiki
Check https://r0ttenbeef.github.io/BlackMega-VM for more detailed information about setting up the host machine and things to do before running the playbook.

## Good to know 
The default BlackMega VM tools are installed using [Chocolaty](https://chocolatey.org/) package manager for windows for easy and fast installation, The tools list are stored in `group_vars/all.yml` as it's easy to be modified as needed.

Be informed that some windows tools are features will be disabled or remove like disabling windows updates using **Windows update blocker tool**, Blocking Microsoft Edge and removing windows bloatware using [Windows10Debloater](https://github.com/Sycnex/Windows10Debloater) which is working for windows 11 perfectly.

## Requirements
Just an up and running up-to-date windows 10 or windows 11 virtual machine without bother doing any extra installation.
Also make sure to take a snapshot before running the playbook in case any damages could happen.

## Notice
Don't hesitate to give me your suggestions and submitting issues and pull requests.
