# Intro to the CLI

#### What is a CLI?

- Command-line interface
- The interface used to configure Cisco devices

Connect to devices via a rollover cables
Use a terminal emulator to actually connect to the CLI

First boots to User EXEC mode: Router>
EXEC mode is limited
enter: enable to enter privileged mode

#### running-config / startup-config

- There are two seperate config files kept on the device at once

	- Running-config: the current, ative config file on the device. As you enter commands in the CLI, you edit the active config

	- Startup-config: the configuration file that will be loaded upon restart of the device

#### Modes Review

Router> 		: user EXEC mode

Router# 		: privileged EXEC mode

Router(config)# : global config mode

#### Command Review

Router> enable
(used to enter privileged EXEC mode)

Router# configure terminal
(used to enter global config mode)

Router(config)# enable password 
(configures a password to protect privileged exec mode)

Router(config)# service password-encryption
(encrypts the enable password and other passwords)

Router(config)# enable secret
(configures a more secure, always encrypted enable password)

Router(config)# run
(executes a privileged exec level command from global config mode)

Router(config)# no
(removes the command)

Router(config)# show running-config
(displays the current, active config file)

Router(config)# show startup-config
(displays the saved config file which will be loaded if the device is restarted)

