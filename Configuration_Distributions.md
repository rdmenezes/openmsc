
# Introduction #

OpenMSC provides several distributions from which the user can select:
  * Gaussian
  * Exponential
  * Linear
  * Gamma
  * Erlang
  * Uniform (real)
  * Uniform (integer)

The distributions are used to determine the UE starting times as well as for the latencies between each communication descriptor. All distributions are implemented using the Boost::Math library.

In order to illustrate how different distributions affect the starting times of UEs, the following example MSC is used as an input to OpenMSC:

![https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/openmsc.png](https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/openmsc.png)

The corresponding configuration file is as follows:

```
version = "0.2";

openmscConfig:
{
	seed = 1;
	numOfUesPerBs = 50;	# Number of UEs per BS, maximal 99
	numOfBss = 30;		# Number of base-stations, maximal 999

	ueActivity-Dist = "gaussian";
	ueActivity-Dist-Min = 1.0;		# only used for unform_real (float) & unform_int (int)
	ueActivity-Dist-Max = 5.0;		# only used for unform_real (float) & unform_int (int)
	ueActivity-Dist-Lambda = 0.5;	# only used for exponential
	ueActivity-Dist-Alpha = 0.75;	# only used for gamma (float) and erlang (int)
	ueActivity-Dist-Beta = 2.0;		# only used for gamma (float) and erlang (int)
	ueActivity-Dist-Mu = 3.0;		# only used for gaussian
	ueActivity-Dist-Sigma = 1.0;	# only used for gaussian
};
```

# Distributions #
## Exponential ##
To use an exponential distribution for the UE communication description starting times, `openmsc.cfg` needs to receive the entry
```
ueActivity-Dist = "exponential";
```

together with the lambda parameter, e.g.:
```
ueActivity-Dist-Lambda = 0.5;
```

The resulting distribution plot with the EventIDs on the x-axis and the emulator's run-time on the y-axis is given below.
![https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/exponential_Lambda-0.5.png](https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/exponential_Lambda-0.5.png)

More information about how the gaussian distribution is implemented in Boost
[follow this link](http://www.boost.org/doc/libs/1_54_0/libs/math/doc/html/math_toolkit/dist_ref/dists/exp_dist.html)

## Gaussian (Normal) ##
To use a Gaussian distribution for the UE communication description starting times, `openmsc.cfg` needs to receive the entry
```
ueActivity-Dist = "gaussian";
```

together with the parameters mu and sigma, e.g.:
```
ueActivity-Dist-Mu = 3.0;
ueActivity-Dist-Sigma = 1.0;
```

The resulting distribution plot with the EventIDs on the x-axis and the emulator's run-time on the y-axis is given below.
![https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/gaussian_Mean-3_Sigma-1.png](https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/gaussian_Mean-3_Sigma-1.png)

More information about how the gaussian distribution is implemented in Boost [follow this link](http://www.boost.org/doc/libs/1_54_0/libs/math/doc/html/math_toolkit/dist_ref/dists/normal_dist.html).

## Gamma ##
To use a Gamma distribution for the UE communication description starting times, `openmsc.cfg` needs to receive the entry
```
ueActivity-Dist = "gamma";
```

together with the parameters mu and sigma, e.g.:
```
ueActivity-Dist-Alpha = 0.75;
ueActivity-Dist-Beta = 2.0;
```

The resulting distribution plot with the EventIDs on the x-axis and the emulator's run-time on the y-axis is given below.
![https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/gamma_Alpha-0.75_Beta-2.png](https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/gamma_Alpha-0.75_Beta-2.png)

More info about how this distribution is implemented in Boost [follow this link](http://www.boost.org/doc/libs/1_54_0/libs/math/doc/html/math_toolkit/dist_ref/dists/gamma_dist.html).

## Uniform (Integer) ##
To use a uniform distribution (that generates integer numbers) for the UE communication description starting times, `openmsc.cfg` needs to receive the entry
```
ueActivity-Dist = "uniform_int";
```

together with the parameters min and max, e.g.:
```
ueActivity-Dist-Min = 1;
ueActivity-Dist-Max = 5;
```

The resulting distribution plot with the EventIDs on the x-axis and the emulator's run-time on the y-axis is given below.
![https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/uniform_int_Min-1_Max-5.png](https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/uniform_int_Min-1_Max-5.png)

## Uniform (Real) ##
To use a uniform distribution (that generates real numbers) for the UE communication description starting times, `openmsc.cfg` needs to receive the entry
```
ueActivity-Dist = "uniform_real";
```

together with the parameters min and max, e.g.:
```
ueActivity-Dist-Min = 1.0;
ueActivity-Dist-Max = 5.0;
```

The resulting distribution plot with the EventIDs on the x-axis and the emulator's run-time on the y-axis is given below.
![https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/uniform_real_Min-1.0_Max-5.0.png](https://googledrive.com/host/0B0ig-Rw0sniLUF92Nlp1RncxalU/uniform_real_Min-1.0_Max-5.0.png)