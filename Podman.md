# Podman, using

I am hoping this doc is not really needed.

## Updating Podman 
```
# Check for special config files which Podman needs to runas non-root
[ ! -f /etc/subuid ] && echo "ERROR: /etc/subuid not found"
[ ! -f /etc/subgid ] && echo "ERROR: /etc/subgid not found"

# Still trying to figure out which part(s) of this is necessary
# [ ! -f /home/$USER/.config/containers/storage.conf ] && { echo "runroot = /run/user/$NEWUID"; }
rm -rf /home/$USER/.local/share/containers/storage
podman system reset
```

## changing UID (as a reference)
```
sudo su -
OLDUID=
OLDGRP=
NEWUID=
NEWGRP=
USER=jradtke
usermod -u $NEWUID $USER
usermod -g $NEWGRP $USER
find /home/$USER -group $OLDGRP -exec chgrp -h $NEWGRP {} \;
find /home/$USER -user $OLDUID -exec chgrp -h $NEWUID {} \;
```

