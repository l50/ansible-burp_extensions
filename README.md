# ansible-burp_extensions
[![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/l50/ansible-burp_extensions/blob/master/LICENSE)

Ansible playbook to install Burp extensions. It also maintains a user options file (through templating) and a project options file, 
which help to have a uniform experience across different systems.

In case you've stumbled across this project, it's my first Ansible role
so try not to judge too harshly. Consider it a work in progress, and let
me know how I can make it better.

### Setup
Install dependencies:
```
ansible-galaxy install -r requirements.yml
```
Create directory for logs:
```
sudo mkdir /var/log/$USER && sudo chown -R <your username>:<suitable group for your user> /var/log/$USER
```

Make sure `~/.ansible.cfg` has the following in it:
```
[defaults]
log_path = /var/log/<your username>/ansible.log
```

### To run:
1. Run this command:
```
ansible-playbook -vvv site.yml
```
2. Once the command has finished, load the `~/burp_extensions/burp_user_options.json` file in burp for the user options

### Included Burp Extensions
* ActiveScan++
* AuthMatrix
* Autorize
* Backslash-Powered-Scanner
* CO2
* Content-Type Converter
* Copy As Python-Requests
* Freddy, Deserialization Bug Finder - Detect and exploit serialisation libs and APIs
* HUNT Methodology
* HUNT Scanner
* J2EEScan
* JSON Web Tokens - Used to manipulate JWTs
* Logger++
* Paramalyzer
* Retire.js
* SAML Raider - Used for testing SAML infrastructure for vulnerabilities
* Upload Scanner

### To add a new extension
1. Create a new role based on one of the other roles
2. Change the path in `tasks/main.yml` to match the new role name
3. Change the names of the extension in `vars/main.yml` to match the new role name
4. Update the `bapp_link` link in `vars/main.yml`
5. Add the new extension to `templates/burp_user_options.json.tmpl` under the `extensions` section

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
- [x] Add Paramalyzer
- [x] Add Logger++
- [x] Add ActiveScan++
- [x] Add Backslash Powered Scanner
- [x] Add J2EEScan
- [x] Add AuthMatrix
- [x] Add Upload Scanner
- [x] Add Copy As Python-Requests
- [x] Add JSON Web Tokens
- [x] Add Freddy, Deserialization Bug Finder
- [x] Unarchive bapps
- [x] Add burp_user_options template
- [x] Move auto-update to bash script template
- [x] Add logging and log rotation
- [] Unit tests
- [] DRY code up
- [] Travis-CI
