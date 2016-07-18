# COREst Clients
## Client scripts and wrappers to interact with the Core Services API

### Python (`py/`)

```
git clone git@gitlab.dmdmedia.net:/techops/corest-clients
cd corest-clients/py
```

#### Requirements installation of `pip`

> This option requires the user to have sudo/root privileges in order to install OS-level python libraries:
##### Centos
```
sudo yum -y install python-pip
```
##### Ubuntu
```
sudo apt-get install python-pip
```

#### Requirements installation without `virtualenv`

> This option requires the user to have sudo/root privileges in order to install OS-level python libraries:

```
sudo pip install -r requirements.txt
```

#### Requirements installation With `virtualenv`

> This option requires an existing `virtualenv`:

```
source path/to/virtualenv/bin/activate
pip install -r requirements.txt
```

> Now that we have the required libraries installed, we must source the `setenv`
script to provide credenatials.  The Core Services API authenticates against
the DMEDIA domain, same domain used for Gmail and VPN.

```
[jcamou@localhost py]$ source setenv 
DMEDIA user: 
jesus.camou
password: 
```

> You should now be able to run the CLI helper:

```
[jcamou@localhost py]$ python client.py 
Usage: client.py - COREst CLI helper

  DNS calls:
    change_view         Submit changes for a given DNS domain view.
                        Takes three arguments: domain, name and json file.
                        Ex. client.py change_view demandmedia.com internal file.json
    get_change_history  Get the change history of the user administered domains.
    get_change_status   Get the status of the change with the given change ID.
                        Ex. client.py get_change_status 577430d9dcfe91408c561c65
    get_domains         Get all the user administered domains.
    list_view           List a user-administrated domain view.
                        Ex. client.py list_view dmdmedia.net internal
    get_record          Get the record for a given zone, view and domain.
                        Ex. client.py dmdmedia.net internal gitlab.dmdmedia.net

  LDAP calls:
    add_ssh_key         Adds an ssh public key to the user LDAP account.
                        Ex. client.py add_ssh_key "ssh-rsa AAAAB..."
    del_ssh_keyo        Deletes an ssh public key from the user LDAP account.
                        Ex. client.py del_ssh_key "ssh-rsa AAAAB..."
    get_ssh_keys        Gets all the ssh public keys from the user LDAP account.
    get_user_info       Retrieves user info in a given domain.

```
