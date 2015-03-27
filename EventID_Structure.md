

# Structure of a Single Event ID #
a particular communication
descriptor is represented as a single numeric EventID due to the requirement of most data mining algorithms which are able to work with numbers only. Therefore, OpenMSC translates each communication descriptor entity into a single unique integer representation, then concatenates these representations in a standardised way, as shown in Table I.

| **Field** | Source | Destination | Protocol Type | Primitive Name | Information Element | IE Value |
|:----------|:-------|:------------|:--------------|:---------------|:--------------------|:---------|
| **Size** | 5 | 5 | 2 | 2 | 2 | 3 |

Each communication descriptor has a source NE and a
destination NE which exchange information using primitives
that are standardised. As primitive names can be the same
across multiple protocols, OpenMSC distinguishes between the
protocol type and primitive name. Each primitive has various
Information Elements (IEs) which hold particular values. The
total length of the generated EventID is 19 due to the maxi-
mal length of the data type unsigned long long in all
programming languages.

The source and destination NEs are represented by a five
digit long integer values. The integer representations are being
allocated on an iterative basis where an unknown NE will
receive a number which is incremented by one, when compared
to its predecessor NE. The only exceptions are UEs and BSs,
as they are treated differently by OpenMSC.

In case of a BS, OpenMSC calculates a BS EventID, ID<sub>bs</sub>, by:

ID<sub>bs</sub> = 100 × BS(m)

with m ∈ Z and 0 < m. For instance, if the total number of BS<sub>s</sub>, n<sub>bs</sub>, equals 50, the five digit long numerical representation of the second BS (m = 2) is `00200`. The numerical UE representation is calculated as follows:

ID<sub>ue</sub> = 100 · BS(m) + UE(n)

with m, n ∈ Z and 0 < m, n. For m = 2 and n = 45, the corresponding UE identifier ID<sub>ue</sub> would be `00245`. All other NEs receive a unique integer in the range of 1 through 99. This ensures that the five digit long numerical representation of a NE is always unique.

The only limitation by generating the EventID as described above is the total number of NEs, primitives and IEs that can be used in the entire emulation while ensuring a unique integer representation for every piece of information. However, with 999 BSs, 99 UEs at each BS, 99 non BS or UE NEs, it is ensured that OpenMSC still provides enough flexibility to generate data-streams emulating rather large networks. Obviously, OpenMSC users could implement their own data-type of length larger than 19, allowing everyone to arbitrarily increase the network size defined in the MSC. However, this is not the objective of OpenMSC.