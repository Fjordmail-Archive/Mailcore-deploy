# Mailcore-deploy

## Description

1. Checks if [RoundCube](https://github.com/roundcube/roundcubemail/releases/tag/1.4.11) version is latest;
2. Fetch/update custom changes to skin and lang ([RC-Skin-app.sol.dk](https://github.com/Fjordmail/RC-Skin-app.sol.dk)) and back up original RC files;
3. Fetch/update plugins: [RC-Plugin-wblist](https://github.com/Fjordmail/RC-Plugin-wblist), [RC-Plugin-spamlevel](https://github.com/Fjordmail/RC-Plugin-spamlevel);
4. Fetch/update [RAIM](https://github.com/Fjordmail/RAIM);
5. Fetch/update [RC-Plugin-recurrent](https://github.com/Fjordmail/RC-Plugin-recurrent).


## Usage

```console
Usage: ./deploy repo
Available repo:
        Sol.dk-RC
        Wemail-RC
```

## Example

```console
$ ./deploy Sol.dk-RC
UPDATING WEBMAIL: app.sol.dk

Updating Roundcube:
Already up to date.

Updating skin and lang:
Already up to date.

Updating RC-Plugin-wblist:
Already up to date.

Updating RC-Plugin-spamlevel:
Already up to date.

Updating RAIM:
Already up to date.

Updating RC-Plugin-recurrent:
Already up to date.
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
│   ├── plugins/ # Only showing custom plugins
│   │   ├── recurrent -> ../../plugins/RC-Plugin-Recurrent-app.sol.dk/
│   │   ├── spamlevel/ -> ../../plugins/RC-Plugin-spamlevel/
│   │   └── wblist -> ../../plugins/RC-Plugin-wblist/
│   └── program/
│       └── localization/
│           └── da_DK/
│               ├── labels.inc.original
│               └── labels.inc -> ../../../skins/app.sol.dk/program/localization/da_DK/labels.inc # Each file in skin repo is linked to from rc_root
├── app.wemail.no/ # RC root for Wemail.no
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
├── plugins/ # Plugin repos
│   ├── raim-app.sol.dk/ # Repo: RAIM, built for Sol
│   │   └── packages/
│   │       ├── account/
│   │       │   └── build/
│   │       ├── password-reset/
│   │       │   ├── .env -> ../../../../config/app.sol.dk/raim_password-reset.env
│   │       │   └── build/
│   │       ├── payment-page/
│   │       ├── registration/
│   │       │   ├── .env -> ../../../../config/app.sol.dk/raim_registration.env
│   │       │   └── build/
│   │       └── shared/
│   │           └── src/
│   │               └── config.js -> ../../../../../config/app.sol.dk/raim_shared_config.js
│   ├── raim-app.wemail.no/ # Repo: RAIM, built for Wemail
│   ├── RC-Plugin-Recurrent-app.sol.dk/ # Repo: RC-Plugin-Recurrent, configured for Sol
│   │   └── vendor/
│   │       ├── Config.php -> ../../../config/app.sol.dk/recurrent-Config.php
│   │       └── spa -> ../../raim-app.sol.dk/packages/account/build/
│   ├── RC-Plugin-Recurrent-app.wemail.no/ # Repo: RC-Plugin-Recurrent, configured for Wemail
│   ├── RC-Plugin-spamlevel/ # Repo: RC-Plugin-spamlevel
│   └── RC-Plugin-wblist/ # Repo: RC-Plugin-wblist
└── skins/ # Skin repos
    ├── app.sol.dk/ # Repo: RC-Skin-app.sol.dk
    └── app.wemail.no/ # Repo: RC-Skin-app.wemail.no
```
