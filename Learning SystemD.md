Systemd is a software suite that provides system components for Linux operating systems, It is used to keep Linux systems similar in use and configuration. It is a system and service manager. A init system used to bootstrap the user space and manage user processes. It also provides replacements for various daemons and utilities including device management, login management, network management, and event logging. The name its self adheres to the Unix convention of naming daemons by appending the letter d. It is also a play on the term "System D" which refers to a persons ability to adapt and improvise.

**The history of systemD

Fedora Linux was the first major Linux distro to make the switch to SystemD, replacing Upstart. They liked it better due to SystemD providing extensive parallelization during startup and better management of processes. 

It was a software engineer team at Red Hat who initially developed SystemD going by the names  Lennart Poettering and Kay Sievers. This was in 2010. Poettering made a blog post in April of 2010 titled "Rethinking PID 1", Introducing an experimental version of what would later become SystemD. They sought to surpass the efficiency of the init daemon in several ways. They wanted a better software framework for handing dependencies to be able to run more processes concurrently or in parallel during system boot and to reduce the computational overhead of the shell.

**How it all works, to my understanding

There are Unit files that describe how a service, mount point, device or other system resource should be managed.

There are several different types of units:
* Services units (`.service`): Manage services or daemons
* target units (`.target`): Group units together (similar to run levels)
* socket units (`.socket`): Define and manage socket based services
* Mount units (`.mount`): Handle file system mounts
* Timer units (`.timer`): Manage scheduled tasks (like cron jobs)
* We can find these unit files in `/etc/systemd/system` and `/lib/systemd/system/`

Systemd targets:

 * Common targets
	 * multi-user.target (multi-user, non-graphical mode)
	 * graphical.target (multi user with GUI)
	 * reboot.target (reboot the system)
	 * shutdown.target (shut down the system)

Systemd dependency management:

* systemd handles the dependencies between services, if you want to start a service, systemd will ensure that all dependencies needed for it are started first.
* There are directives like `After=` `Before=` `Requieres=` and `Wants=`
* An example would be if `httpd.service` depends on `network.target`, Systemd will ensure that network service starts before `hyypd` does.

**Common commands and management

* Starting a service:

		`sudo systemctl start service_name`

* Stopping a service:

		`sudo systemctl stop service_name`

* Enabling a service to start at boot:

		`sudo systemctl enable service_name`

* Disabling a service

		`sudo systemctl disable service_name`

* Checking the status of a service:

		`sudo systemctl status service name`

* Viewing most recent logs:

		`journalctl -xe`

* View logs for a specific service:

		`journalctl -u service_name`

**SystemD facts

Systemd is the first process to start during boot (PID 1). It takes over control from the bootloader and starts necessary services.

Default target: The default target is specified in `/etc/systemd/system/default.target`, which is typically a symbolic link to a specific target like `multi-user.target` or `graphical.target`.

Systemd can use socket activation to start services on demand as well for situations where a certain service may only be needed at certain time, like a web server that might now need to start until there is a incoming HTTP request.

Systemd offers the ability to automatically restart services as they fail, You are able to configure this with the `Restart=` directive in the services's unit file.
```ini
[service]
Restart=always
```

**Example of a simple service unit file

```ini 
[Unit]
Description=My Sample Service
After=network.target

[Service]
ExecStart=/usr/bin/myapp
Restart=always

[Install]
WantedBy=multi-user.target

```

[Unit] describes the service, including dependencies like `After=network.target`
[Service] Defines the executable command and restart behavior
[Install] Specifies which target the service should be enable under, such as `multi-user.target`

The bootloader loads the kernel into memory and hands over control to the kernel. Then the kernel initializes hardware and mounts the root filesystem, the kernel then starts the init process, which is Systemd (PID 1). SystemD is the first user-space process.

The process goes as following
(1) Kernel Loads → 
(2) Systemd Init → 
(3) Target: basic.target → 
(4) Network & Filesystems → 
(5) Multi-user or Graphical Target → 
(6) Services start (login, web server, etc.) → 
(7) System Fully Up

![[Pasted image 20250113115712.png]]`

[[2025-01-13 (third day, still going strong]]