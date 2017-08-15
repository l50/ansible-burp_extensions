# ansible-burp_extensions
[![License](http://img.shields.io/:license-mit-blue.svg)](http://doge.mit-license.org)

Ansible playbook to install Burp extensions.

In case you've stumbled across this project, it's my first Ansible role
so try not to judge too harshly. Consider it a work in progress, and let
me know how I can make it better.

### Install dependency:
```
ansible-galaxy install -r requirements.yml -p roles
```

### To run:
```
ansible-playbook site.yml
# If you need to specify your sudo password:
ansible-playbook site.yml --ask-sudo-pass
```

### Included Burp Extensions
* Burp CO2
* HUNT Methodology
* HUNT Scanner
* Retire.js
* XSS Validator

### Limitations
Tested on OS X && Ubuntu 16.04
You need to be sure that the PATH for the version of python you're using
with Ansible is set properly in the crontab:
```crontab -e```
```PATH=<your path>``` <- put this at the top of the file and save it.

### Something Missing?
Let me know: jayson.e.grace@gmail.com

### TODO:
- [x] Modularize
- [x] Make friendly with other OS's
- [x] Figure out how to get latest release of an extension from github
  if offered
- [x] Create cronjob to destroy and rebuild every week
- [] Add Content-Type Converter
- [] Add CSRF Scanner
- [] Add J2EEScan
- [] Add Paramalyzer
- [] Travis-CI

## License
MIT
