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

| Model                         | Parameters                      | Handles negative rate |
| :---------------------------- | :------------------------------ | :-------------------- |
| analytiskontodimas_2004       | a, tmin, tmax                   |      ✔️ Yes           |
| ashrafi1_2018                 | a, b, c                         |      ✔️ Yes           |
| ashrafi2_2018                 | a, b, c                         |      ✔️ Yes           |
| ashrafi3_2018                 | a, b, c                         |      ✔️ Yes           |
| ashrafi4_2018                 | a, b, c                         |      ✔️ Yes           |
| ashrafi5_2018                 | a, b, c                         |      ✔️ Yes           |
| atkin_2005                    | a, b, c                         |      ✔️ Yes           |
| beta_2012                     | rmax, tmin, tmax, a, b          |       ❌ No           |
| betatypesimplified_2008       | rmax, tmin, tmax                |       ❌ No           |
| boatman_2017                  | a, b, c                         |      ✔️ Yes           |
| briere1_1999                  | a, tmin, tmax                   |       ❌ No           |
| briere1simplified_1999        | a, tmin, tmax                   |       ❌ No           |
| briere2_1999                  | a, tmin, tmax, b                |       ❌ No           |
| briere2simplified_1999        | a, tmin, tmax, b                |       ❌ No           |
| briereextended_2021           | a, tmin, tmax, b, c             |       ❌ No           |
| briereextendedsimplified_2021 | a, tmin, tmax, b, c             |       ❌ No           |
| delong_2017                   | b0, e, eh, th                   |       ❌ No           |
| deutsch_2008                  | a, b, c, d                      |      ✔️ Yes           |
| eubank_1973                   | a, b, c                         |      ✔️ Yes           |
| flextpc_2024                  | a, b, c, d                      |      ✔️ Yes           |
| flinn_1991                    | a, b                            |       ❌ No           |
| gaussian_1987                 | rmax, topt, a                   |       ❌ No           |
| gaussianmodified_2006         | rmax, topt, a, b                |       ❌ No           |
| hinshelwood_1947              | a, e                            |       ❌ No           |
| janisch1_1925                 | a, b                            |      ✔️ Yes           |
| janisch2_1925                 | a, b, c                         |      ✔️ Yes           |
| joehnk_2008                   | a, b, c                         |      ✔️ Yes           |
| johnsonlewin_1946             | a, b, c                         |       ❌ No           |
| kamykowski_1985               | a, b, c                         |      ✔️ Yes           |
| lactin2_1995                  | a, b, tmax, d                   |       ❌ No           |
| lobry_1991                    | rmax, tmin, tmax                |       ❌ No           |
| mitchell_2009                 | a, b, c                         |       ❌ No           |
| oneill_1972                   | a, b, c                         |      ✔️ Yes           |
| pawar_2018                    | a, b, c                         |      ✔️ Yes           |
| quadratic_2008                | a, b, c                         |      ✔️ Yes           |
| ratkowsky_1983                | a, tmin, tmax                   |       ❌ No           |
| rezende_2019                  | a, b, c                         |       ❌ No           |
| rosso_1993                    | rmax, tmin, topt, tmax          |       ❌ No           |
| sharpeschoolfull_1981         | r_tref, e, el, eh, tl, th, tref |       ❌ No           |
| sharpeschoolhigh_1981         | r_tref, e, eh, th, tref         |       ❌ No           |
| sharpeschoollow_1981          | r_tref, e, el, tl, tref         |       ❌ No           |
| spain_1982                    | a, b, c                         |      ✔️ Yes           |
| stinner_1974                  | a, b, c                         |      ✔️ Yes           |
| taylorsexton_1972             | a, b, c                         |      ✔️ Yes           |
| thomas_2012                   | a, b, c                         |      ✔️ Yes           |
| thomas_2017                   | a, b, c                         |      ✔️ Yes           |
| tomlinsonphillips_2015        | a, b, c                         |       ❌ No           |
| warrendreyer_2006             | a, b, c                         |       ❌ No           |
| weibull_1995                  | a, b, c                         |       ❌ No           |

### Contributing
Please consider opening an issue to add new thermal performance curve models, both here and for [rTPC](https://github.com/padpadpadpad/rTPC/issues).

### Citation
If you use these functions, please cite the authors of the rTPC package:

>Padfield D, O’Sullivan H, Windram F (2024). rTPC: Fitting and Analysing Thermal Performance Curves. R package version 1.0.7, https://padpadpadpad.github.io/rTPC/, https://github.com/padpadpadpad/rTPC
