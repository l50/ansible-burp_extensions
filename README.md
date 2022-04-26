# ansible-burp_extensions

[![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/l50/ansible-burp_extensions/blob/master/LICENSE)
[![Pre-Commit](https://github.com/l50/ansible-burp_extensions/actions/workflows/pre-commit.yaml/badge.svg)](https://github.com/l50/ansible-burp_extensions/actions/workflows/pre-commit.yaml)

Ansible playbook to install Burp extensions.
It also maintains a user options file and project options file (via template),
which help to facilitate a uniform experience across different systems.

In case you've stumbled across this project, it's my first Ansible role
so try not to judge too harshly. Consider it a work in progress, and let
me know how I can make it better.

---

## Setup

Install dependencies:

```bash
ansible-galaxy install -r requirements.yml
```

If you want to use XSSHunter to check for Blind XSS
in the referer header, be sure to set `referer_blind_xss`
in `group_vars/all` to "true". You will also need to specify
the script to run using `xss_hunter_script`.
A default example is provided that you can modify or replace completely.

---

## Run it

1. Run this command:

   ```bash
   ansible-playbook site.yml
   ```

2. Once the command has finished, load
   the `~/burp_extensions/burp_user_options.json` file
   in burp for the user options and the
   `~/burp_extensions/burp_project_options.json` file
   for the project options.

---

## Included Burp Extensions

- ActiveScan++
- AuthMatrix
- Autorize
- Backslash-Powered-Scanner
- CO2
- ~~Collaborator Everywhere~~
  - Shove Burp Collaborator payloads into all inputs
  - Breaks a lot of things
- Content-Type Converter
- Copy As Python-Requests
- EsPReSSO
- ~~Freddy, Deserialization Bug Finder~~
  - Detect and exploit serialization libs and APIs
  - Currently missing from the bapp store
- GraphQL Raider
- HTTP Request Smuggler
- HUNT Methodology
- HUNT Scanner
- J2EEScan
- JSON Web Tokens - Used to manipulate JWTs
- Logger++
- Paramalyzer
- Retire.js
- SAML Raider - Used for testing SAML infrastructure for vulnerabilities
- Upload Scanner

---

## Add New Extension

1. Create a new role based on one of the other roles
   (be sure to use a role that matches the language of the extension)
2. Change the path in `tasks/main.yml` to match the new role name
3. Change the names of the extension in `vars/main.yml` to match the new role name
4. Update the `bapp_link` link in `vars/main.yml`
5. Add the new extension to
   `templates/burp_user_options.json.tmpl`
   under the `extensions` section
6. Add the new role to `site.yml`
7. Be sure to update the list of Included Burp Extensions in the `README.md`

---

## Limitations

You need to be sure that the PATH for the version of python you're using
with Ansible is set properly in the crontab:

```bash
crontab -e
```

Put this at the top of the file and save it:
`PATH=<your path>`

If you have a proxy, put your proxy settings in here too:

```bash
http_proxy=<proxy>
```
