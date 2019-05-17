# DonkeyPunch
DonkeyPunch is a `systemd` service that keeps a reverse SSH tunnelled port open on a remote server.  By default it is setup to forward the local SSH port to some remote machine port for accessing beyond a firewall or NAT.

---

# Automatic Installation
## `install` :: (`bin/`)
- Before using the installation script, be sure to setup your config(s) based on the `example.conf` file in `scr/share/conf/`:
  - Rename `example.conf` to `yourhost.conf`, then edit the file to your liking.
  - Anything with a `.conf` extension will get automatically installed as a service configuration by the `install` script.
- Next, The easiest way to install and uninstall DonkeyPunch is with the install script:
  - Fisrt `cd donkeypunch` to enter the release directory.
  - Next `chmod +x bin/install` to allow execution.
  - Finally do `sudo bin/install` to install it.

---

# Manually Install DonkeyPunch
## `donkeypunch` :: (`src/bin/`)
- Install this script in the `/usr/local/bin` folder or whatever.
- Next `chmod +x /usr/local/bin/donkeypunch` to make it executable or whatever.


## `donkeypunch@.service` :: (`src/share/service/`)
- Install this service template in the `/etc/systemd/system` folder or whatever.
- Be sure to replace the two tokens `__ENV_PATH__` and `__SERVICE_PATH__` to match your system or whatever:
  - The default `__ENV_PATH_` would be `/etc/default`.
  - The default `__SERVICE_PATH__` would be `/usr/local/bin/donkeypunch`.


## `donkeypunch@example` :: (`src/share/conf/`)
- These configuration files should be stored in the `/etc/default` folder or whatever.
- Multiple hosts and configurations can be configured by adding new `donkeypunch@newexamplehost` files that match the construction of the provided example.  Make sure you have all the configuration options included.

---

# Running DonkeyPunch
Once everything has been installed to the correct folders DonkeyPunch can be started.  Start it using `service donkeypunch@yourhostbla start` or `systemctl start donkeypunch@yetanotherhost` for example.  It can be set to run at boot as well using `systemctl` (google it) and has been configured to wait on the network services before launching.  As a final note, like all `systemd` services it will log to your default system log and each configuration will have its own PID (check `/var/run` to see them).
