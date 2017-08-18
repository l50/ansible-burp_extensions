# ansible-burp_extensions
[![License](http://img.shields.io/:license-mit-blue.svg)](http://doge.mit-license.org)

Ansible playbook to install Burp extensions.

In case you've stumbled across this project, it's my first Ansible role
so try not to judge too harshly. Consider it a work in progress, and let
me know how I can make it better.

### To run:
```
ansible-playbook site.yml
```

### Included Burp Extensions
* CO2
* HUNT Methodology
* HUNT Scanner
* Retire.js
* XSS Validator
* Content-Type Converter
* CSRF Scanner (currently broken -
  https://github.com/ah8r/csrf/issues/9)
* Paramalyzer

### Limitations
Tested on OS X && Ubuntu 16.04
You need to be sure that the PATH for the version of python you're using
with Ansible is set properly in the crontab:
```crontab -e```
```PATH=<your path>``` <- put this at the top of the file and save it.
If you have a proxy, put your proxy settings in here too:
```http_proxy=<proxy>```
etc.

### Something Missing?
Let me know: jayson.e.grace@gmail.com

### TODO:
- [x] Modularize
- [x] Make friendly with other OS's
- [x] Figure out how to get latest release of an extension from github
  if offered
- [x] Create cronjob to destroy and rebuild every week
- [x] Add Content-Type Converter
- [x] Add CSRF Scanner
- [x] Add Paramalyzer
- [] Add J2EEScan
- [] Travis-CI

## License
MIT
