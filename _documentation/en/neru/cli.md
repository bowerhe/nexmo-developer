---
title: NeRu CLI
description: This documentation describes the NeRu CLI
meta_title: NeRu CLI
---

# NeRu CLI

`neru` is the NeRu command-line interface that is required for managing and deploying your applications from the terminal.

## Installation

### Mac

#### Intel

```sh
curl -O https://api-eu.vonage.com/v1/neru/i/neru-59e69cd7-neru-cli-install-dist/neru-cli_darwin_amd64/neru
chmod +x ./neru 
sudo mv ./neru /usr/local/bin
```

#### M1 (ARM)

```sh
curl -O https://api-eu.vonage.com/v1/neru/i/neru-59e69cd7-neru-cli-install-dist/neru-cli_darwin_arm64/neru
chmod +x ./neru 
sudo mv ./neru /usr/local/bin
```

### Windows

```sh
mkdir .neru
cd .neru
curl -O https://api-eu.vonage.com/v1/neru/i/neru-59e69cd7-neru-cli-install-dist/neru-cli_windows_amd64/neru.exe
setx PATH "%PATH%;%cd%"
```
Close and reopen command prompt to reload your `PATH`.

### Linux

```sh
curl -O https://api-eu.vonage.com/v1/neru/i/neru-59e69cd7-neru-cli-install-dist/neru-cli_linux_amd64/neru
chmod +x ./neru 
sudo mv ./neru /usr/local/bin
```

## Setup your Account 

Configure your account using your Vonage API key and secret which can be obtained from the [Dashboard](https://dashboard.nexmo.com):

```sh
neru configure 
```

The command will ask for your a default region as well as your Vonage API key and secret which you can get from the from the [API Dashboard](https://dashboard.nexmo.com/).

## Updating the CLI

To update the CLI run: 

```sh
neru version
```

This will print our the current version of the CLI you have installed. If there is a newer version available, you will be prompted to install it.



