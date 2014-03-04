# Loggregator

## Duplicate log messages for an application appear occassionally 

* Loggreator may resend one or more log lines to the cf command line client (or syslog drains) if the logging process is restarted (due to CF deployment upgrade, restart of DEA, etc.) This happens very infrequently.
