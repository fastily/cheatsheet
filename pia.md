## Connecting
```bash
# Connect to the currently selected region
piactl connect

# Disconnect from PIA
piactl disconnect
```

## Get info/status
```bash
# List available regions
piactl get regions

# Show currently set region
piactl get region

# Show current VPN ip (must be connected for this to work)
piactl get vpnip

# Check if connected to VPN
piactl get connectionstate
```

## Settings
```bash
# Specify a region to connect to.
piactl set region '<REGION_NAME>'

# Permanently enable daemon in background (normally only running when UI is active)
piactl background enable
```