# stanTPC: Thermal performance curves in Stan

<!-- badges: start -->
[![License: GPL
v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
<!-- badges: end -->

`stanTPC` provides a Stan translation of [rTPC](https://padpadpadpad.github.io/rTPC/) for
functions for fitting thermal performance curves to data.

### How to use
Copy the file `tpc-models.stanfunctions` to the directory containing the `.stan` file that
will fit a thermal performance curve. In the functions block, insert the following:
```
functions {
  ...
  #include tpc-models.stanfunctions
  ...
}
```

### Contributing
Please consider opening an issue to add new thermal performance curve models, both here and for [rTPC](https://github.com/padpadpadpad/rTPC/issues).

### Citation
If you use these functions, please cite the authors of the rTPC package:

>Padfield D, O’Sullivan H, Windram F (2024). rTPC: Fitting and Analysing Thermal Performance Curves. R package version 1.0.7, https://padpadpadpad.github.io/rTPC/, https://github.com/padpadpadpad/rTPC
