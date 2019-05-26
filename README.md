# ansible-burp_extensions
[![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/l50/ansible-burp_extensions/blob/master/LICENSE)

Ansible playbook to install Burp extensions.

In case you've stumbled across this project, it's my first Ansible role
so try not to judge too harshly. Consider it a work in progress, and let
me know how I can make it better.

### To run:
```
ansible-playbook site.yml
```

### Included Burp Extensions
* ActiveScan++ (bapp)
* AuthMatrix (bapp)
* Backslash-Powered-Scanner (bapp)
* CO2 (bapp)
* Content-Type Converter (bapp)
* Copy As Python-Requests (bapp)
* Freddy, Deserialization Bug Finder (bapp) - Detect and exploit serialisation libs and APIs
* HUNT Methodology
* HUNT Scanner
* J2EEScan (bapp)
* JSON Web Tokens (bapp) - Used to manipulate a JWT
* Logger++ (bapp)
* Paramalyzer (bapp)
* Retire.js (bapp)
* Upload Scanner (bapp)
* XSS Validator - An issue exists on OSX because they moved phantomjs to
  cask. Commented out of site.yml for now since I'm not really using it
  much anyway.

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
- [] Add burp_user_options template
- [] Redo auto updates to create backup of previous, and then override ~/burpExtensions after all work has been done
- [] Travis-CI

## License
MIT
