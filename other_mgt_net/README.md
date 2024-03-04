# Other Management Network (and possibly routing instance)
If your access to system management tools like DNS, NTP, RADIUS, SYSLOG, etc.
lives somewhere that is not accessible from the out-of-band management
interface (em0, fxp0, etc.) and mgmt_junos routing instance, add those
details to this property set.  Also remember to set the `is_enabled` flag to
`true`.

This is a property set only.  It will be used by other configlets where
necessary.  However, the Jinja file included here shows the lines that must be
included at the top of every configlet that's derived from this repo and
references the IP address and routing instance that the device uses to source
requests to these various services.