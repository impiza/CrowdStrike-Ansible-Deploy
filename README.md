# CrowdStrike-Ansible-Deploy

Please find the files inside /etc/ansible
```md
/etc/ansible/
├── activate.yml
├── ansible.cfg
├── copy.yml
├── csstatus.yml
├── hosts
├── install.yml
└── startservice.yml

```
Please find my [CrowdStrike Community]([Community](https://community.crowdstrike.com/members/impiza-1947 "Community") profile  
Detailed instructions will be update soon
## Recording
[![asciicast](https://asciinema.org/a/RHDY2KTi9w93yBMuoogPrYAbp.svg)](https://asciinema.org/a/RHDY2KTi9w93yBMuoogPrYAbp)

This is result of my CrowdStrike Deployment using Ansible playbook.
```bash
root@ansible:/etc/ansible# ls activate.yml ansible.cfg copy.yml csstatus.yml hosts install.yml startservice.yml testing
root@ansible:/etc/ansible# ansible-playbook copy.yml
PLAY [Ansible copy] *********************************************************************************************************
TASK [Gathering Facts] ******************************************************************************************************
ok: [192.168.4.222]
ok: [192.168.4.221]
TASK [Copy files from control node to remote node] **************************************************************************
changed: [192.168.4.222]
changed: [192.168.4.221]
PLAY RECAP ******************************************************************************************************************
192.168.4.221 : ok=2 changed=1 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
192.168.4.222 : ok=2 changed=1 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
root@ansible:/etc/ansible# ansible-playbook install.yml PLAY
[Ansible apt installer] ************************************************************************************************
TASK [Gathering Facts] ******************************************************************************************************
ok: [192.168.4.222]
ok: [192.168.4.221]
TASK [Ansible install cs deb file from local] *******************************************************************************
changed: [192.168.4.222]
changed: [192.168.4.221]
PLAY RECAP ******************************************************************************************************************
192.168.4.221 : ok=2 changed=1 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
192.168.4.222 : ok=2 changed=1 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
root@ansible:/etc/ansible# ansible-playbook activate.yml PLAY
[nodes] ****************************************************************************************************************
TASK [Gathering Facts] ******************************************************************************************************
ok: [192.168.4.222]
ok: [192.168.4.221]
TASK [Activate cs.] *********************************************************************************************************
changed: [192.168.4.222]
changed: [192.168.4.221]
PLAY RECAP ******************************************************************************************************************
192.168.4.221 : ok=2 changed=1 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
192.168.4.222 : ok=2 changed=1 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
root@ansible:/etc/ansible# ansible-playbook csstatus.yml
PLAY [nodes] ****************************************************************************************************************
TASK [Gathering Facts] ******************************************************************************************************
ok: [192.168.4.222]
ok: [192.168.4.221]
TASK [Check if cs process is running] ***************************************************************************************
fatal: [192.168.4.222]: FAILED! => {"changed": true, "cmd": "sudo ps -e | grep falcon-sensor", "delta": "0:00:00.085307", "en d": "2024-02-13 16:49:33.041668", "failed_when_result": true, "msg": "non-zero return code", "rc": 1, "start": "2024-02-13 16 :49:32.956361", "stderr": "", "stderr_lines": [], "stdout": "", "stdout_lines": []} fatal: [192.168.4.221]: FAILED! => {"changed": true, "cmd": "sudo ps -e | grep falcon-sensor", "delta": "0:00:00.076670", "en d": "2024-02-13 16:49:33.060303", "failed_when_result": true, "msg": "non-zero return code", "rc": 1, "start": "2024-02-13 16 :49:32.983633", "stderr": "", "stderr_lines": [], "stdout": "", "stdout_lines": []} PLAY RECAP ******************************************************************************************************************
192.168.4.221 : ok=1 changed=0 unreachable=0 failed=1 skipped=0 rescued=0 ignored=0
192.168.4.222 : ok=1 changed=0 unreachable=0 failed=1 skipped=0 rescued=0 ignored=0
root@ansible:/etc/ansible# ansible-playbook startservice.yml
PLAY [nodes] ****************************************************************************************************************
TASK [Gathering Facts] ******************************************************************************************************
ok: [192.168.4.222]
ok: [192.168.4.221]
TASK [cs current status.] ***************************************************************************************************
changed: [192.168.4.221]
changed: [192.168.4.222]
PLAY RECAP ******************************************************************************************************************
192.168.4.221 : ok=2 changed=1 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
192.168.4.222 : ok=2 changed=1 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
root@ansible:/etc/ansible# ansible-playbook csstatus.yml
PLAY [nodes] ****************************************************************************************************************
TASK [Gathering Facts] ******************************************************************************************************
ok: [192.168.4.221]
ok: [192.168.4.222]
TASK [Check if cs process is running] ***************************************************************************************
changed: [192.168.4.222]
changed: [192.168.4.221]
TASK [Display cs process status] ********************************************************************************************
ok: [192.168.4.221] => { "process_status.stdout_lines": [ " 3261 ? 00:00:05 falcon-sensor-b" ] }
ok: [192.168.4.222] => { "process_status.stdout_lines": [ " 2875 ? 00:00:06 falcon-sensor-b" ] }
PLAY RECAP ******************************************************************************************************************
192.168.4.221 : ok=3 changed=1 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
192.168.4.222 : ok=3 changed=1 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
root@ansible:/etc/ansible

```
