# Mailcore-deploy

## Description

Checks if webmail and plugins are up to date.  
If the webmail is to be updated, creates a backup.

## Usage

```sh
Usage: ./deploy repo
Available repo:
        Sol.dk-RC
        Wemail-RC
```

## Todo

* Check if links are valid with `test -e`;
* Use `pull` instead of `clone` and stop backing up: we have `git` for that;
* Check if `should_be_updated` works as intended and do some testing.

## Tree

```console
.
├── app.sol.dk/ # RC root for Sol.dk - some directories are omitted
│   ├── config -> ../config/app.sol.dk
│   ├── instance/
│   │   ├── password-reset -> ../../plugins/raim-app.sol.dk/packages/password-reset/build
│   │   └── registration -> ../../plugins/raim-app.sol.dk/packages/registration/build
│   └── plugins/
│       ├── archive/
│       ├── automatic_addressbook/
│       ├── calendar/
│       ├── export_provisioning/
│       ├── hotkeys/
│       ├── identicon/
│       ├── jqueryui/
│       ├── libkolab/
│       ├── mailia_expire/
│       ├── mailia_info/
│       ├── mailia_login/
│       ├── managesieve/
│       ├── message_highlight/
│       ├── password/
│       ├── persistent_login/
│       ├── recurrent -> ../../plugins/RC-Plugin-Recurrent-app.sol.dk
│       ├── spamlevel/
│       ├── swipe/
│       └── wblist -> ../../plugins/RC-Plugin-wblist
├── app.wemail.no/ # RC root for Wemail
├── config/ # Config for each webmail is stored here
│   ├── app.sol.dk/
│   │   ├── config.inc.php
│   │   ├── config.inc.php.sample
│   │   ├── custom.inc.php
│   │   ├── defaults.inc.php
│   │   ├── mimetypes.php
│   │   ├── raim_password-reset.env
│   │   ├── raim_registration.env
│   │   ├── raim_shared_config.js
│   │   └── recurrent-Config.php
│   └── app.wemail.no/
├── deploy # This deploy script
├── deploy_keys/
└── plugins/ # Each custom plugin is stored here
    ├── raim-app.sol.dk/
    │   ├── packages/
    │   │   ├── account/
    │   │   │   └── build/
    │   │   ├── password-reset/
    │   │   │   ├── .env -> ../../../../config/app.sol.dk/raim_password-reset.env
    │   │   │   └── build/
    │   │   ├── payment-page/
    │   │   ├── registration/
    │   │   │   ├── .env -> ../../../../config/app.sol.dk/raim_registration.env
    │   │   │   └── build/
    │   │   └── shared/
    │   │       └── src/
    │   │           └── config.js -> ../../../../../config/app.sol.dk/raim_shared_config.js
    ├── RC-Plugin-Recurrent-app.sol.dk/
    │   └── vendor/
    │       ├── Config.php -> ../../../config/app.sol.dk/recurrent-Config.php
    │       └── spa -> ../../raim-app.sol.dk/packages/account/build
    └── RC-Plugin-wblist
```
