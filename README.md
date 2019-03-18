# DonkeyPunch
DonkeyPunch is a `systemd` service that keeps a reverse SSH tunnelled port open on a remote server.  By default it is setup to forward the local SSH port to some remote machine port for accessing beyond a firewall or NAT.

---

# Install DonkeyPunch
## `donkeypunch`
- Install this script in the `/usr/local/bin` folder or whatever.
- Next `chmod +x /usr/local/bin/donkeypunch` to make it executable or whatever.


## `donkeypunch@.service`
- Install this service template in the `/etc/systemd/system` folder or whatever.


## `donkeypunch@example`
- These configuration files should be stored in the `/etc/default` folder or whatever.
- Multiple hosts and configurations can be configured by adding new `donkeypunch@newexamplehost` files that match the construction of the provided example.  Make sure you have all the configuration options included.

---

# Running DonkeyPunch
Once everything has been installed to the correct folders DonkeyPunch can be started.  Start it using `service donkeypunch@yourhostbla start` or `systemctl start donkeypunch@yetanotherhost` for example.  It can be set to run at boot as well using `systemctl` (google it) and has been configured to wait on the network services before launching.  As a final note, like all `systemd` services it will log to your default system log and each configuration will have its own PID (check `/var/run` to see them).
