# Mailcore-deploy

## Description

1. Fetch/update [RoundCube](https://github.com/roundcube/roundcubemail/releases/tag/1.4.11) to latest from upstream;
2. Fetch/update custom skin ([RC-Skin](https://github.com/Fjordmail/RC-Skin)) and back up original RC files;
3. Fetch/update custom lang ([RC-Lang](https://github.com/Fjordmail/RC-Lang)) and back up original RC files;
4. Fetch/update plugins: [RC-Plugin-wblist](https://github.com/Fjordmail/RC-Plugin-wblist), [RC-Plugin-spamlevel](https://github.com/Fjordmail/RC-Plugin-spamlevel), [RC-Plugin-mailcore_loglgin](https://github.com/Fjordmail/RC-Plugin-mailcore_loglogin), [RC-Plugin-managesieve](https://github.com/Fjordmail/RC-Plugin-managesieve);
5. Fetch/update [RAIM](https://github.com/Fjordmail/RAIM);
6. Fetch/update [RC-Plugin-recurrent](https://github.com/Fjordmail/RC-Plugin-recurrent).


## Usage

```console
Usage: ./deploy repo destination
Available repo:
        Sol.dk-RC
        Wemail-RC
```

## Example

```console
$ ./deploy Sol.dk-RC app.sol.dk/
UPDATING WEBMAIL: app.sol.dk

Updating Roundcube:
Already up to date.

Updating skin and lang:
remote: Enumerating objects: 13, done.
remote: Counting objects: 100% (13/13), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 7 (delta 4), reused 7 (delta 4), pack-reused 0
Unpacking objects: 100% (7/7), done.
From github.com:Fjordmail/RC-Skin-app.sol.dk
   0e7d9f5..ab38642  master     -> origin/master
Updating 0e7d9f5..ab38642
Fast-forward
 skins/elastic/styles/layout.less | 2 +-
 skins/elastic/styles/styles.css  | 2 +-
 2 files changed, 2 insertions(+), 2 deletions(-)

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

* Try to reuse get_plugin for RC-Plugin-recurrent

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
│   │   ├── mailcore_loglogin -> ../../plugins/RC-Plugin-mailcore_loglogin/
│   │   ├── managesieve/
│   │   │   ├── config.inc.php -> ../../config/managesieve.conf
│   │   │   └── skins/
│   │   │       └── sol -> elastic/
│   │   ├── recurrent -> ../../plugins/RC-Plugin-Recurrent-app.sol.dk/
│   │   ├── spamlevel/ -> ../../plugins/RC-Plugin-spamlevel/
│   │   └── wblist -> ../../plugins/RC-Plugin-wblist/
│   ├── program/
│   │   └── localization/
│   │       └── da_DK/
│   │           ├── labels.inc.original
│   │           └── labels.inc -> ../../../skins/app.sol.dk/program/localization/da_DK/labels.inc
│   └── skins/
│       ├── sol -> ../../repos/RC-Skin/skins/sol/
│       └── wemail -> ../../repos/RC-Skin/skins/wemail/
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
└── repos/ # Repos with RAIM, plugins, sking and langs
    ├── raim-app.sol.dk/ # RAIM, built for Sol
    │   └── packages/
    │       ├── account/
    │       │   └── build/
    │       ├── password-reset/
    │       │   ├── .env -> ../../../../config/app.sol.dk/raim_password-reset.env
    │       │   └── build/
    │       ├── payment-page/
    │       ├── registration/
    │       │   ├── .env -> ../../../../config/app.sol.dk/raim_registration.env
    │       │   └── build/
    │       └── shared/
    │           └── src/
    │               └── config.js -> ../../../../../config/app.sol.dk/raim_shared_config.js
    ├── raim-app.wemail.no/ # RAIM, built for Wemail
    ├── RC-Lang/ # Custom nb, nn, dk, and en
    ├── RC-Plugin-Recurrent-app.sol.dk/ # Recurrent plugin configured for Sol
    │   └── vendor/
    │       ├── Config.php -> ../../../config/app.sol.dk/recurrent-Config.php
    │       └── spa -> ../../raim-app.sol.dk/packages/account/build/
    ├── RC-Plugin-Recurrent-app.wemail.no/ # recurrent plugin configured for Wemail
    ├── RC-Plugin-spamlevel/
    ├── RC-Plugin-wblist/
    └── RC-Skin/
```
