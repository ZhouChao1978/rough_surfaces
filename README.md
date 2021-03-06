## Analysis of rough surfaces

Fast Fourier Transform based power spectrum analysis for rough surfaces.

### Usage 
Our basic imports are
```
import numpy as np
import import surfanalysis as sa
```
A radially averaged (isotropic) roughness power spectrum is obtained as
```
# load array with surface height data
h = np.loadtxt(fname)

# sepcify lattice size
dxy = 5.0E-5

# apply Hann window
window = True

# obtain radially averaged roughness spectrum and frequencies
f, C = sa.radially_averaged_psd(h, dxy, window)
```
Correspondingly, power spectra can be averaged along each axis 
```
fx, Cx = sa.axis_averaged_psd(h, dxy, window, 0)
fy, Cy = sa.axis_averaged_psd(h, dxy, window, 1)
```
The Hurst exponents and roughness scaling exponents can be approximated by a fitting function as
```
pref, hurst = sa.self_affine_psd_fit(f, C)
prefy, hursty = sa.self_affine_psd_fit(fy, Cy, onedim=True)
prefx, hurstx = sa.self_affine_psd_fit(fx, Cx, onedim=True)
```
See `example_analysis.py` for a more complete overview and the provided plotting functions.

## Examples
An isotropic surface is characterized by a near-ideal straight line radially averaged PSD and same-slope curves for the angularly averaged spectra.
<p align="left">
  <img src="https://raw.githubusercontent.com/plang85/rough_surfaces/master/doc/isotropic.png" height="400">
  <br/>
</p>
An anisotropic surface is characterized by a less linear radially averaged PSD and different-slope curves for the angularly averaged spectra.
<p align="left">
  <img src="https://raw.githubusercontent.com/plang85/rough_surfaces/master/doc/anisotropic.png" height="400">
  <br/>
</p>
