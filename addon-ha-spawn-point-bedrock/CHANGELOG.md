<!-- https://developers.home-assistant.io/docs/add-ons/presentation#keeping-a-changelog -->

## 2024.10.0

- Fixed Download for LATEST Version to use User-Agent for curl
- Bump actions/checkout from 4.2.0 to 4.2.1
- Bump frenck/action-addon-linter from 2.15 to 2.17
- Bump home-assistant/builder from 2024.03.5 to 2024.08.2

## 2024.1.0 New Year Cleanup

- Removed double banner printout
- Changed License to MIT
- Bump home-assistant/builder from 2023.09.0 to 2023.12.0

## 2023.12.1 New Dedicated Server Version

- Bump to Dedicated Server Version 1.20.50.3

## 2023.11.2 Downgrade Versions

- The version can be now downgraded with the version config entry.

## 2023.11.1 New Version Schema

- Switched to new version schema
- Some internal house keeping

## 0.0.7 - Docker Config Hotfix

- Fixed Linter Problem building the remote Docker image

## 0.0.6 - Docker Config Hotfix

- Fixed Linter Problem building the Docker image

## 0.0.5 - Docker Image Hotfix

- Fixed Problem building the Docker image

## 0.0.4 - Faster Docker Image

- Removed update of baseimage during docker creation
- Fixed URL in log banner
- Fixed some log typos

## 0.0.3 - Beeing Operator

- Added new config entries for user permissions in the configuration UI
- Moved **Allowed User List** to normal configuration entries
- Fixed some log printouts

## 0.0.2 - Allowed Users

- Added new config entries in the UI for the configuration of allowed users
- Removed some of the initial log print outs

## 0.0.1 - Initial release

- Used debian stable image as base
- Added logo and icon
- Add an apparmor profile
