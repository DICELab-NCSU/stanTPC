# stanTPC: Thermal performance curves in Stan

<!-- badges: start -->
[![License: GPL
v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
<!-- badges: end -->

`stanTPC` provides a Stan translation of [rTPC](https://padpadpadpad.github.io/rTPC/) for
functions for fitting thermal performance curves to data.

### How to use
#### Make functions available to your Stan code
Copy the file `tpc-models.stanfunctions` to the directory containing the `.stan` file that
will fit a thermal performance curve. In the functions block, insert the following:
```
functions {
  ...
  #include tpc-models.stanfunctions
  ...
}
```

#### Add parameters to the `model` block
You will need to add the parameters of the model you want to use to the `model` block. The parameters are:

| Parameter | Typical interpretation                  |
| :-------- | :-------------------------------------- |
| `a`       | scale / intercept / rate constant       |
| `b`       | shape / slope / curvature               |
| `c`       | shape / location                        |
| `d`       | shape / exponent                        |
| `rmax`    | maximum rate                            |
| `tmin`    | lower thermal limit                     |
| `tmax`    | upper thermal limit                     |
| `topt`    | optimum temperature                     |
| `e`       | activation energy                       |
| `el`      | low-temp inactivation energy            |
| `eh`      | high-temp inactivation energy           |
| `tl`      | low-temp inactivation temperature       |
| `th`      | high-temp inactivation temperature      |
| `tref`    | reference temperature                   |
| `b0`      | baseline rate                           |

The models are:

| Model                         | Parameters                      |
|:------------------------------|:--------------------------------|
| analytiskontodimas_2004       | a, tmin, tmax                   |
| ashrafi1_2018                 | a, b, c                         |
| ashrafi2_2018                 | a, b, c                         |
| ashrafi3_2018                 | a, b, c                         |
| ashrafi4_2018                 | a, b, c                         |
| ashrafi5_2018                 | a, b, c                         |
| atkin_2005                    | a, b, c                         |
| beta_2012                     | rmax, tmin, tmax, a, b          |
| betatypesimplified_2008       | rmax, tmin, tmax                |
| boatman_2017                  | a, b, c                         |
| briere1_1999                  | a, tmin, tmax                   |
| briere1simplified_1999        | a, tmin, tmax                   |
| briere2_1999                  | a, tmin, tmax, b                |
| briere2simplified_1999        | a, tmin, tmax, b                |
| briereextended_2021           | a, tmin, tmax, b, c             |
| briereextendedsimplified_2021 | a, tmin, tmax, b, c             |
| delong_2017                   | b0, e, eh, th                   |
| deutsch_2008                  | a, b, c, d                      |
| eubank_1973                   | a, b, c                         |
| flextpc_2024                  | a, b, c, d                      |
| flinn_1991                    | a, b                            |
| gaussian_1987                 | rmax, topt, a                   |
| gaussianmodified_2006         | rmax, topt, a, b                |
| hinshelwood_1947              | a, e                            |
| janisch1_1925                 | a, b                            |
| janisch2_1925                 | a, b, c                         |
| joehnk_2008                   | a, b, c                         |
| johnsonlewin_1946             | a, b, c                         |
| kamykowski_1985               | a, b, c                         |
| lactin2_1995                  | a, b, tmax, d                   |
| lobry_1991                    | rmax, tmin, tmax                |
| mitchell_2009                 | a, b, c                         |
| oneill_1972                   | a, b, c                         |
| pawar_2018                    | a, b, c                         |
| quadratic_2008                | a, b, c                         |
| ratkowsky_1983                | a, tmin, tmax                   |
| rezende_2019                  | a, b, c                         |
| rosso_1993                    | rmax, tmin, topt, tmax          |
| sharpeschoolfull_1981         | r_tref, e, el, eh, tl, th, tref |
| sharpeschoolhigh_1981         | r_tref, e, eh, th, tref         |
| sharpeschoollow_1981          | r_tref, e, el, tl, tref         |
| spain_1982                    | a, b, c                         |
| stinner_1974                  | a, b, c                         |
| taylorsexton_1972             | a, b, c                         |
| thomas_2012                   | a, b, c                         |
| thomas_2017                   | a, b, c                         |
| tomlinsonphillips_2015        | a, b, c                         |
| warrendreyer_2006             | a, b, c                         |
| weibull_1995                  | a, b, c                         |

### Contributing
Please consider opening an issue to add new thermal performance curve models, both here and for [rTPC](https://github.com/padpadpadpad/rTPC/issues).

### Citation
If you use these functions, please cite the authors of the rTPC package:

>Padfield D, O’Sullivan H, Windram F (2024). rTPC: Fitting and Analysing Thermal Performance Curves. R package version 1.0.7, https://padpadpadpad.github.io/rTPC/, https://github.com/padpadpadpad/rTPC
