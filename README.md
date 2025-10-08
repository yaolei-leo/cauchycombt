# Cauchy combination test
This is a package performs Cauchy combination test (cct) developed by [Liu et al. (2025)](https://www.tandfonline.com/doi/full/10.1080/01621459.2018.1554485). The code is the python reimplementation of [CCT.R](https://github.com/xihaoli/STAAR/blob/master/R/CCT.R) in [STAAR](https://github.com/xihaoli/STAAR) project.

## Tutorial
To perform the Cauchy combination test, user need to supply a numpy array with p-values. Several quality controls will be conducted, including check NaN value(s) and all the p-values are between 0 and 1 (exactly 0 and 1 are not allowed). User can also supply weight for each p-value for the test. Similarly, quality controls will be conducted, including check: NaN values, negative value, the sum of all weight values is not 1. Error will be raised if violating the these quality controls, so check your input before perform the analysis.

### Example run
Test with p-value array only, all the p-values will have exactly same weight.
```python
>>> from cauchycombt import cct
>>> pval_arr = np.array([0.43, 0.86, 0.003, 0.0001, 1E-4, 0.19])
>>> cct(pval_arr)
0.00029510164688062446
```

Test with p-value array and weight.
```python
>>> from cauchycombt import cct
>>> pval_arr = np.array([0.43, 0.86, 0.003, 0.0001, 1E-4, 0.19])
>>> weight_arr = np.array([0.31, 0.35, 0.01, 0.01, 0.01, 0.31])
>>> cct(pval_arr, weight_arr)
0.004934287256275538
```
