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

* Use `pull` instead of `clone` for RAIM? Partial build?

## Tree

Omitting most common files:

```bash
.
├── app.sol.dk/ # RC root for Sol.dk
│   ├── config -> ../config/app.sol.dk
│   ├── instance/
│   │   ├── password-reset -> ../../plugins/raim-app.sol.dk/packages/password-reset/build/
│   │   └── registration -> ../../plugins/raim-app.sol.dk/packages/registration/build/
│   ├── plugins/
│   │   ├── recurrent -> ../../plugins/RC-Plugin-Recurrent-app.sol.dk/
│   │   ├── spamlevel/ -> ../../plugins/RC-Plugin-spamlevel/
│   │   └── wblist -> ../../plugins/RC-Plugin-wblist/
│   └── program/
│       └── localization/
│       └── da_DK/
│           ├── labels.inc.original
│           └── labels.inc -> ../../../skins/app.sol.dk/program/localization/da_DK/labels.inc
├── app.wemail.no/
├── config/
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
├── plugins/ # Each custom plugin is stored here
│   ├── raim-app.sol.dk/
│   │   ├── packages/
│   │   │   ├── account/
│   │   │   │   └── build/
│   │   │   ├── password-reset/
│   │   │   │   ├── .env -> ../../../../config/app.sol.dk/raim_password-reset.env
│   │   │   │   └── build/
│   │   │   ├── payment-page/
│   │   │   ├── registration/
│   │   │   │   ├── .env -> ../../../../config/app.sol.dk/raim_registration.env
│   │   │   │   └── build/
│   │   │   └── shared/
│   │   │       └── src/
│   │   │           └── config.js -> ../../../../../config/app.sol.dk/raim_shared_config.js
│   ├── RC-Plugin-Recurrent-app.sol.dk/
│   │   └── vendor/
│   │       ├── Config.php -> ../../../config/app.sol.dk/recurrent-Config.php
│   │       └── spa -> ../../raim-app.sol.dk/packages/account/build/
│   ├── RC-Plugin-spamlevel/
│   └── RC-Plugin-wblist/
└── skins/
    ├── app.sol.dk/
    └── app.wemail.no/
```
