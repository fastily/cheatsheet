## Change Config
```
configure
<COMMAND TO EXECUTE 1>
<COMMAND TO EXECUTE 2>
<COMMAND TO EXECUTE 3...>
commit
save
exit
```

## ssh
```bash
# Disable password-based auth
set service ssh disable-password-authentication

# Install Public Key
# Copy public key to the router (e.g. in /tmp/blah.pub), then do:
loadkey '<USERNAME>' '<PATH_TO_PUBLIC_KEY>'
```

## show
```bash
# List user info
show system login user '<USERNAME>'

# List interfaces
show interfaces
```

## upgrade
```bash
# show current version
show version

# show current storage
show system image storage

# upgrade image
add system image 'https://dl.ubnt.com/.../firmware.tar'

# confirm it worked; be sure to reboot when done
show system image
```