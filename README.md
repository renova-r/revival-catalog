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

Validation uses R 4.6.2 on Linux and compares frozen outputs with the historical baseline. Each release includes its check log and NOTE remarks.

## Install

```r
install.packages(c("prettyR", "BBSSL", "SamplerCompare", "RSGHB", "plogr", "reactablefmtr"), repos = c(
  Renova = "https://renova-r.r-universe.dev",
  CRAN = "https://cloud.r-project.org"
))
```

Each package repository includes its changes, original authors and license.

[Project home](https://github.com/renova-r) · [R-universe](https://renova-r.r-universe.dev/)
