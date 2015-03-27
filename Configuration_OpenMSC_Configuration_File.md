

# Introduction #
In order to configure OpenMSC, the libconfig library is leveraged using the C++ API.

An example configuration file is provided in the doc/example SVN folder.

# Mandatory Fields #

  * numOfUesPerBs
  * numOfBss
  * cycleTime

## numOfUesPerBs ##
This parameter specifies how many user equipments (UEs) are attached to each base-station (BS). In other words, each BS has the same number of UEs.

The maximal number of BSs is 999.

## numOfBss ##
This parameter specifies the total number of base-stations in the network.

The maximal number of UEs in the network is 99.

## cycleTime ##
This parameter specifies a time frame in which all UEs pick one use-case from the MSCgen configuration file. For instance, if _numOfUesPerBs = 5_ and _numOfBss = 2_ there are 10 UEs in total. Assuming _cycleTime_ is set to 50 OpenMSC determines at time _t = 0s_ 50 randomly selected slots _s_ between 0s < _s_ < 50s in which each UE will start generating numbers based on the use-case specified in [openmsc.msc](Configuration_MSCgen_File_Convention.md). After 50s OpenMSC is selecting 50 new slots again.

# Information Elements and Their Values #