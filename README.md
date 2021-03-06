# netbox_topology

Fork from https://github.com/bashioo/netbox_topology

[**Update**] patchfile updated. This is working with netbox **2.7.3**


Patch to apply to a netbox installation to add beautiful topology view to sites

Once installed your individual site's pages should look like this:

![Screenshot](docs/screenshot-site.png "Screenshot of site's page")

This module allows to create and delete connections between interfaces via control panel:

![Screenshot control panel](docs/screenshot-panel.png "Screenshot of the control panel")

## INSTALL:

1. clone git repo

```
git clone https://github.com/kevinpm/netbox_topology.git
```

2. run install.sh, sudo might be required to get access to netbox installation directory:

```
cd netbox_topology
sudo ./install.sh
```

3. restart netbox via supervisord or apache/nginx (or even the docker container(s)) depending on your installation

```
sudo supervisorctl restart netbox
sudo service apache2 restart
sudo docker restart <container-name>
docker-compose restart
```

4. open django admin web-interface and create a custom text field named "coordinates" under dcim->device model

![Screenshot django setup](docs/screenshot-customfield.png "Screenshot of django setup")

**Coordinates format** x;y

5. modify NETBOXPATH/netbox/static/js/topology_config.json to include your list on roles to hide from the topology view. You will need to add new list of cables to shown under shown_cables
Constants are defined here
```
    "shown_cables": [
        cat5e,
        cat6,
        cat6a,
        cat7
    ]
```

please note that the list should include SLUGs, not names. please check that json is valid.

6. let me know if there are any issues - https://github.com/kevinpm/netbox_topology/issues



## UNINSTALL:

```
sudo ./uninstall.sh
```

OR if your installation is GIT based (Option 2 from Netbox installation guide):

```
cd /opt/netbox
git checkout .
```
**TODO:** Add patch to netbox-docker
