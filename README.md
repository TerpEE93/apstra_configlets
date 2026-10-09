# Apstra Configlets
This is a repo of simple Apstra configlets.  Each folder includes a configlet
in Jinja2 format (so you can copy/paste it into the Apstra configlet editor),
the same configlet in JSON format (so you can simply import it into Apstra),
and if necessary, a property set.  Feel free to use them as examples or
deploy them as part of your own Apstra-managed infrastructure.  Just be
aware that my standard disclaimer applies:

> There is no warranty, expressed or implied, with this repo. You get what you
pay for, and what you see here is free. Use carefully, and at your own risk.

If you're good with that, then enjoy!

## What you'll find...
Each folder contains one or more configlets, and possibly property sets, that
demonstrate how to configure something outside of the Apstra reference
design.  Some examples relate to basic services like DNS and NTP, while others
relate to device hardening -- disabling the root account, for example.  Files
are named accordingly:

| Filename                 | Description                               |
|--------------------------|-------------------------------------------|
| `<configlet>_<nos>.j2`   | Jinja2 formatted configlet for copy/paste |
| `<configlet>_<nos>.json` | JSON formatted configlet for import       |
| `<configlet>.prop.json`  | JSON formatted property set               |
| `<configlet>.prop.yaml`  | YAML formatted property set               |
| `README.md`              | The relevant README for the configlet     |
| `changelog.md`           | The changelog.  What did you think?       |
