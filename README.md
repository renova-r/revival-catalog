# Renova packages

Reviving R software with AI.

| Package | Purpose | Renova version | Validation |
| --- | --- | --- | --- |
| [BBSSL](https://github.com/renova-r/BBSSL) | Bayesian Bootstrap Spike-and-Slab LASSO | [0.1.0.9001](https://github.com/renova-r/BBSSL/releases/tag/renova-0.1.0.9001) | 0 errors, 0 warnings, 2 notes; 6 cases match |
| [SamplerCompare](https://github.com/renova-r/SamplerCompare) | Compare MCMC samplers | [1.3.4.9001](https://github.com/renova-r/SamplerCompare/releases/tag/renova-1.3.4.9001) | 0 errors, 0 warnings, 3 notes; 29 cases match |
| [RSGHB](https://github.com/renova-r/RSGHB) | Hierarchical Bayesian estimation | [1.2.2.9001](https://github.com/renova-r/RSGHB/releases/tag/renova-1.2.2.9001) | 0 errors, 0 warnings, 3 notes; 4 cases match |
| [prettyR](https://github.com/renova-r/prettyR) | Descriptive statistics and HTML output | [2.2.3.9002](https://github.com/renova-r/prettyR/releases/tag/renova-2.2.3.9002) | 0 errors, 0 warnings, 4 notes; 34 cases match |
| [plogr](https://github.com/renova-r/plogr) | C++ logging headers | [0.2.0.9001](https://github.com/renova-r/plogr/releases/tag/renova-0.2.0.9001) | 0 errors, 0 warnings, 2 notes; 1 case matches |
| [reactablefmtr](https://github.com/renova-r/reactablefmtr) | Interactive table styling and formatting | [2.0.0.9001](https://github.com/renova-r/reactablefmtr/releases/tag/renova-2.0.0.9001) | 0 errors, 0 warnings, 2 notes; 62 cases match |
| [clv](https://github.com/renova-r/clv) | Internal and external cluster validation measures and cluster stability functions for results of the cluster package and user-defined clustering algorithms. | [0.3.2.5.9001](https://github.com/renova-r/clv/releases/tag/renova-0.3.2.5.9001) | 0 errors, 0 warnings, 2 notes; 17 cases match |
| [RSvgDevice](https://github.com/renova-r/RSvgDevice) | An R graphics device that writes plots as W3C Scalable Vector Graphics (SVG) files. | [0.6.4.4.9001](https://github.com/renova-r/RSvgDevice/releases/tag/renova-0.6.4.4.9001) | 0 errors, 0 warnings, 5 notes; 1 case matches |
| [JRF](https://github.com/renova-r/JRF) | Joint random forests for the simultaneous estimation of multiple related gene networks. | [0.1.4.9001](https://github.com/renova-r/JRF/releases/tag/renova-0.1.4.9001) | 0 errors, 0 warnings, 2 notes; 4 cases match |

Validation uses R 4.6.2 on Linux and compares frozen outputs with the historical baseline. Each release includes its check log and NOTE remarks.

## Install

Choose a package above, then install it with:

```r
install.packages("PACKAGE", repos = c(
  Renova = "https://renova-r.r-universe.dev",
  CRAN = "https://cloud.r-project.org"
))
```

Each package repository includes its changes, original authors and license.

[Project home](https://github.com/renova-r) · [R-universe](https://renova-r.r-universe.dev/)
