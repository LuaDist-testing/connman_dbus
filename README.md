# Get network information with Connman and DBus

This module provides a simple API to query
[Connman](https://01.org/connman/)
using [DBus](http://dbus.freedesktop.org/).

# Requirements

In addition to the requirements specified in the rockspec file, you need
Connman (version 1.33 or higher) and DBus. Note that you may need permissions
to access the Connman DBus interface.

# Installation

This module can be installed with [Luarocks](http://luarocks.org/) by running

    luarocks install connman_dbus

Use the `--local` option in `luarocks` if you don't want or can't install it
system-wide.

# Example

Below is a small example of how to use the module:

```lua
connman = require("connman_dbus")
print(connman.OfflineMode) -- e.g. true

active_service = connman:GetServices()[1]
print(active_service[1])
-- e.g. "/net/connman/service/wifi_12341234_abcdabcd_managed_psk"
active_service_properties = active_service[2]
print(active_service_service.Type)
-- e.g. "wifi"
print(active_service_service.State)
-- e.g. "online"

tech = connman:GetTechnologies()[1]
print(tech[1])
-- e.g. "/net/connman/technology/ethernet"
tech_props = tech[2]
tech_props.Name
-- e.g. "wired"
tech_props.Type
-- e.g. "ethernet"
tech_props.Powered
-- e.g. true
```

# Documentation

The documentation of this module is built using [LDoc](https://stevedonovan.github.io/ldoc/).
A copy of the documentation is already provided in the `doc` folder,
but you can build it from source by running `ldoc .` in the root of the repository.

# Limitations

At the moment, only
the
[Connman Manager API](https://git.kernel.org/pub/scm/network/connman/connman.git/tree/doc/manager-api.txt) is
supported. This is enough to get information about services and technologies,
but does not allow to implement a fully functional client.

# Contributing

Feel free to contribute with pull requests and issue reports, but be advised
that this project is developed in the author's own spare time.
