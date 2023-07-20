# BlackMega-VM
Convert windows virtual machine to a lab for malware analysis using ansible playbooks for automated installation of malware analysis tools and gadgest, Debloating useless windows services to reduce windows traffic noise and overwhelming running processes.

## Good to know 
The default BlackMega VM tools are installed using [Chocolaty](https://chocolatey.org/) package manager for windows for easy and fast installation, The tools list are stored in `group_vars/all.yml` as it's easy to be modified as needed.

Be informed that some windows tools are features will be disabled or remove like disabling windows updates using [Windows update blocker]https://www.sordum.org/9470/windows-update-blocker-v1-8/ tool, Blocking Microsoft Edge and removing windows bloatware using [Windows10Debloater](https://github.com/Sycnex/Windows10Debloater) which is working for windows 11 perfectly.

## Requirements
Just an up and running up-to-date windows 10 or windows 11 virtual machine without bother doing any extra installation, Just your preferred browser.
Also make sure to take a snapshot before running the playbook in case any damages could happen.

## Windows configurations before running
Before running ansible playbook there's some changes to be made on windows machine first.

### Enable Windows Remote Management (WinRM)
Ansible will use WinRM protocol to connect the windows machine.

1. Make the network private
![Pasted image 20230717154700](https://github.com/r0ttenbeef/BlackMega-VM/assets/48027449/e67ca391-d4a3-400b-9d11-605434a14501)

2. Enable WinRM from powershell (Run as Administrator)
```powershell
winrm quickconfig
winrm set winrm/config/service/auth '@{Basic="true"}'
winrm set winrm/config/service '@{AllowUnencrypted="true"}'
```

3. Disable Windows Defender and Firewall
![Pasted image 20230717172211](https://github.com/r0ttenbeef/BlackMega-VM/assets/48027449/1e87666d-2bcb-454b-9bee-e73182a6f4fa)

4. Disable User Account Control Settings (UAC)
![Pasted image 20230718003110](https://github.com/r0ttenbeef/BlackMega-VM/assets/48027449/d0c84f78-ee5e-4f43-bd29-8cb66b32500d)

### Initiate the installation
After cloning the BlackMega VM repository install python **winrm** module.

```bash
pip install -r requirements
```

The hosts credentials should be stored at `hosts.ini` file like following example.

```css
[windows_box]
10.0.20.5

[windows_box:vars]
ansible_user = "admin_user"
ansible_password = "pass123"
ansible_port = 5985
ansible_connection = winrm
ansible_winrm_transport = basic
```

Now you can start ansible playbook.

```bash
ansible-playbook start.yml -i hosts.ini
```
