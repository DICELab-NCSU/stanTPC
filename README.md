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
You will need to add the parameters of the model you want to use to the `model` block. The models are:

| Model                         | Parameters                      | Negative low | Negative high |
| :---------------------------- | :------------------------------ | :----------- | :------------ |
| analytiskontodimas_2004       | a, tmin, tmax                   | no           | no            |
| ashrafi1_2018                 | a, b, c                         | yes          | no            |
| ashrafi2_2018                 | a, b, c                         | yes          | yes           |
| ashrafi3_2018                 | a, b, c                         | no           | no            |
| ashrafi4_2018                 | a, b, c, d                      | yes          | yes           |
| ashrafi5_2018                 | a, b, c, d                      | yes          | yes           |
| atkin_2005                    | r0, a, b                        | no           | no            |
| beta_2012                     | a, b, c, d, e                   | no           | no            |
| betatypesimplified_2008       | rho, alpha, beta                | no           | yes           |
| boatman_2017                  | rmax, tmin, tmax, a, b          | no           | no            |
| briere1_1999                  | tmin, tmax, a                   | no           | no            |
| briere1simplified_1999        | tmin, tmax, a                   | yes          | no            |
| briere2_1999                  | tmin, tmax, a, b                | yes          | no            |
| briere2simplified_1999        | tmin, tmax, a, b                | yes          | no            |
| briereextended_2021           | tmin, tmax, a, b, d             | no           | no            |
| briereextendedsimplified_2021 | tmin, tmax, a, b, d             | no           | no            |
| delong_2017                   | c, eb, ef, tm, ehc              | no           | no            |
| deutsch_2008                  | rmax, topt, ctmax, a            | no           | yes           |
| eubank_1973                   | topt, a, b                      | no           | no            |
| flextpc_2024                  | tmin, tmax, rmax, alpha, beta   | no           | no            |
| flinn_1991                    | a, b, c                         | no           | no            |
| gaussian_1987                 | rmax, topt, a                   | no           | no            |
| gaussianmodified_2006         | rmax, topt, a, b                | no           | no            |
| hinshelwood_1947              | a, e, b, eh                     | no           | yes           |
| janisch1_1925                 | m, a, topt                      | no           | no            |
| janisch2_1925                 | m, a, b, topt                   | no           | no            |
| joehnk_2008                   | rmax, topt, a, b, c             | yes          | yes           |
| johnsonlewin_1946             | r0, e, eh, topt                 | no           | no            |
| kamykowski_1985               | tmin, tmax, a, b, c             | yes          | yes           |
| lactin2_1995                  | a, b, tmax, delta_t             | yes          | yes           |
| lobry_1991                    | rmax, topt, tmin, tmax          | no           | no            |
| mitchell_2009                 | topt, a, b                      | no           | no            |
| oneill_1972                   | rmax, ctmax, topt, q10          | no           | no            |
| pawar_2018                    | r_tref, e, eh, topt, tref       | no           | no            |
| quadratic_2008                | a, b, c                         | yes          | yes           |
| ratkowsky_1983                | tmin, tmax, a, b                | no           | no            |
| rezende_2019                  | q10, a, b, c                    | no           | yes           |
| rosso_1993                    | rmax, topt, tmin, tmax          | no           | yes           |
| sharpeschoolfull_1981         | r_tref, e, el, tl, eh, th, tref | no           | no            |
| sharpeschoolhigh_1981         | r_tref, e, eh, th, tref         | no           | no            |
| sharpeschoollow_1981          | r_tref, e, el, tl, tref         | no           | no            |
| spain_1982                    | a, b, c, r0                     | no           | yes           |
| stinner_1974                  | rmax, topt, a, b                | no           | no            |
| taylorsexton_1972             | rmax, tmin, topt                | no           | yes           |
| thomas_2012                   | a, b, c, tref                   | yes          | yes           |
| thomas_2017                   | a, b, c, d, e                   | yes          | yes           |
| tomlinsonphillips_2015        | a, b, c                         | no           | yes           |
| warrendreyer_2006             | rmax, topt, a                   | no           | no            |
| weibull_1995                  | a, topt, b, c                   | no           | no            |

### Contributing
Please consider opening an issue to add new thermal performance curve models, both here and for [rTPC](https://github.com/padpadpadpad/rTPC/issues).

### Citation
If you use these functions, please cite the authors of the rTPC package:

>Padfield D, O’Sullivan H, Windram F (2024). rTPC: Fitting and Analysing Thermal Performance Curves. R package version 1.0.7, https://padpadpadpad.github.io/rTPC/, https://github.com/padpadpadpad/rTPC
