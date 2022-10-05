# Your First Device API Call
So what exactly can you do with Jane's devices? Well, that depends on their Capabilities! Let's discuss what those are and then use them.

## Device Capabilities
A [Device Capability](../core_concepts/device_capabilities.md) is **a feature or function of a device.**

For example, on a door-lock the `access_codes` capability lets you program pin-codes. These codes then let a user unlock the door without keys.

Each Capability decomposes into `actions`, `properties`, and `events`.

- **Actions** -- things you can do to it.
- **Properties** -- the current state of the device.
- **Events** -- reports from the device describing state transitions.

Taken as a whole, the capabilities of a device descrbie its programmatic interface. At Seam, we work as best we can toward standardizing each capability's API across brands. For example, our lock/unlock actions work the same across brands of door locks.


