# Service Management (user land software management)

init is the first process to be executed by the kernel, but it resides in user land. and is always pid 1.

- sysvinit (classic)
  - running several shell scripts (launch lots of processes)
  - started in serial
  - dependencies expressed as integers

- launchd(macOS)

- systemd (linux) - based on launchd

these don't run shell scripts, they run unit files.
