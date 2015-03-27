

# Introduction #

As the mscgen tool can be used to generate a graphical illustration of the use-cases, the mscgen file convention must not be changed. Therefore, all OpenMSC specific information needed to be added to the mscgen file must follow the mscgen file convention.

# Structure #

## Network Elements ##

Network elements are the communication entities in the MSC. Each network element **must** use a unique name.

## Use-Cases ##

OpenMSC expects exactly one _Success_ use-case and allows the user to specify _n_ failure use-cases. A use-case leverages the block of signals command `--- [ label = "Success" ]` where the label **must** be specified with the word _Success_.

All failure use-cases **must** be specified with `--- [ label = "Failure" ]`.

## Communication Descriptor ##
A communication descriptor defines a single message flow from a source to a destination network element identified by a protocol, a primitive and a list of information elements and their values.

In other words, each line for a use-case in the openmsc.msc file is an individual communication descriptor.

The following example line is used to explain how to set up a single communication description:

> `UE => BS [ label = "Protocol-Primitive_Name(UE_ID,BS_ID)" ]; #latencyDist = {constant} latencyValue={1.0}`

At the moment OpenMSC does not provide the same flexibility as MSCgen does regarding how to write a communication descriptor. In OpenMSC each line **must** have a tailing tab (`\t`) and the communication direction can only be read from left to right, e.g.: `UE => BS`, not `BS <= UE`.

The label receives the protocol and primitive name which **must** be separated by a dash/hyphen. The primitive name can be written using any standard character. OpenMSC treats all characters between `-` and `(` as the primitive name.

The information elements of the primitive are listed within brackets and **must** be separated by a comma.

The latency details for the communication descriptor are separated by a hash sign. Each latency data **must** start with the latency distribution name `latencyDist`, followed by its parameters it required. the values must be given in curly brackets which are separated from the actual detail with an equal sign `=`. If spaces are being used for the latency data (like in the example line) is not important to OpenMSC. At the moment, OpenMSC accepts the following communication descriptor latencies:
  * Constant
  * Gaussian
  * Exponential

Note, all values (time related such as for constant) are read in in milli seconds.