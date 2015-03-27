# Introduction #

OpenMSC provides four levels of debug output which is written to stdout, i.e.:
  * `ERROR`
  * `INFO`
  * `DEBUG`
  * `TRACE`

# Available Debug Levels #

## `ERROR` ##
Only error messages are printed to stdout. If an error occurs, the emulator exits with a value different than `0`.

## `INFO` ##
Only error and info messages are being printed to stdout. Info messages just indicates that the emulator is running and in case a thread ends (which should never been the case), an info message would be printed to stdout.

## `DEBUG` ##
Only error, info and debug messages are being printed to stdout. Note, this mode is only recommended with one or two UEs set up. Debug messages give detailed information about generated times, latency values and emulator internal processing steps to trac down the work-flow.

## `TRACE` ##
If the trace debug level has been selected, all logging messages are being printed to stdout. The trace level allows to see in very high detail what EventIDs are being generated at what time and when they have been sent to the given destination.