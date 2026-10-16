# Mautrix Google Messages for YunoHost

Matrix / Synapse puppeting bridge for Google Messages (SMS, MMS and RCS of an Android phone), packaged for [YunoHost](https://yunohost.org).
Upstream bridge: <https://github.com/mautrix/gmessages> (mautrix-gmessages v26.09, Go / bridgev2).

## ⚠️ Status: looking for testers

This package installs, upgrades and registers with Synapse correctly (tested on YunoHost 12, Debian 12), but **pairing with a phone has not been tested yet**: I don't have an Android phone.

If you have an Android phone with Google Messages as the default SMS app and want to help, please install it and report how it went in the issues (pairing, sending/receiving SMS, MMS, RCS). If it works, I'll propose it to the YunoHost catalog.

Notes:
- iPhone is not supported (Google Messages is Android only).
- On Android without Google services (e.g. /e/OS with microG), the Google Messages app can be installed and SMS/MMS usually work, but RCS depends on Google services. Messages still go through Google's servers between the phone and the bridge.

## Install

```bash
sudo yunohost app install https://github.com/EpicTGuy/mautrix_gmessages_ynh
```

Then, in your Matrix client, open a chat with the bot, send `login qr` and scan the QR code from Google Messages → profile picture → **Device pairing**.

## Features of this package

- Config generated from the upstream example configs (mautrix-go v0.31.0), with a config panel for the main settings.
- Bridge permissions handled from the install questions and the config panel (no duplicate entries when the same account is admin and user).
- Double puppeting enabled automatically when a shared `doublepuppet` appservice is registered in Synapse (`/etc/matrix-<synapse instance>/app-service/doublepuppet.yaml`, see <https://docs.mau.fi/bridges/general/double-puppeting.html>).

Based on the [mautrix_whatsapp_ynh](https://github.com/YunoHost-Apps/mautrix_whatsapp_ynh) package. License: AGPL-3.0-or-later.
