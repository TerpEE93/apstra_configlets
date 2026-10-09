# protect-re_junos:
Last Updated:  2026-10-08

## Configlet and Property Set
This is a solution to implement a basic Protect-RE filter in Junos.  The
configlet builds an IPv4 (family inet) firewall filter named `PROTECT_RE` and
assigns the filter in the `input` direction on interface `lo0.0`.

### Configlet details
The configlet includes a fixed term that allows BGP from the device's
configured BGP peers.  The list of BGP peers is derived automatically from
the device context.  The configlet also includes a fixed term that allows ICMP
for a list of ICMP-types that the user can specify in the property set (see
details below...)

### Property set details
The property set associated with this configlet is a JSON dictionary with the
following elements:

    1. A list of ICMP types we wish to allow to the device
    2. A list of terms to add to the filter.  Each term is a
       dictionary that includes the following keys:
        a. `service`: A descriptive name of the thing we're accepting/blocking
        b. `protocol`: tcp or udp
        c. `port`: The port number associated with the service
        d. `prefixes`: A list of IPv4 prefixes to match as source addresses
        e. `actions`: A list of what to do on a match?  Some actions include
           `accept`, `discard`, `log`, etc.
    3. A list of default actions to take if there is no match above.  If this
       list is left empty, the default action will be `deny` at the end of
       the `PROTECT_RE` filter.

## Caveats
As always, TEST someplace safe first.  It's very easy to mangle or miss a
necessary term in the property set, and remember that the default `default`
action is to deny traffic.  Consider testing with a `[ permit log ]` list
of default actions so you can see what traffic is not explicitly permitted
before the default action, then add what you missed.

This configlet doesn't really handle services that run on both TCP and UDP, or
services that run across multiple ports (e.g. a port-range).  For now, you'll
need to create separate term entries in the services list for TCP, UDP, and any
ports required.

Remember that the list of terms is indeed an ordered list!  If term_A must
appear before term_B to ensure expected behavior, no shadownig, etc., make
sure you add them to the list in the right order.

Finally, this is IPv4 only for now!  No support for IPv6 (family inet6) until
the next version.