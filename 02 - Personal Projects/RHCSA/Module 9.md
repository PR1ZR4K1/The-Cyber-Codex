2024/02/07 17:37
Status: #idea
Tags:

# Control Services and Daemons

The first process that starts (PID 1) is the *systemd* daemon, which provides these features:

- Parallelization capabilities (starting multiple services simultaneously), which increase the boot speed of a system.
- On-demand starting of daemons without requiring a separate service.
- Automatic service dependency management, which can prevent long timeouts. For example, a network-dependent service does not try to start until the network is availaible.
- A method of tracking related processes together by using Linux control groups.

## Service Units Description

A *systemd unit* is an abstract concept to define objects that the system knows how to manage.

A *Unit* has a name and a unit type. 

- Name: Provides a unique identity to the unit
- Type: Enable grouping units together with other similar unit types

The *systemd* daemon uses units to manage different types of objects:

- Service *units* have a .service extension and represent system services. You can use service units to start often-accessed daemons, such as a web server.
- Socket units have a .socket extension and represent inter-process communication (IPC) sockets that *systemd* should monitor
- Path units have a .path extension and delay the activation of a service until a specific file-system change occurs.




---
# References
