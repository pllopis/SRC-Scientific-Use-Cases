# Inputs

## 3G_201804G

Contains SuperCLASS one day set of observations 3G_201804G (205GB).
TODO: Ask Bob about the source

The inputs.ini file must be adjusted for the `fits_path` to point to the directory containing the FITS-IDI files, e.g.:

```
Calibrator_0_1331+305_L-Band_Std_ALL_0.fits    H30_5_1028+6815_L-Band_Std_ALL_0.fits
Calibrator_116_0319+415_L-Band_Std_ALL_0.fits  H32_13_1028+6820_L-Band_Std_ALL_0.fits
Calibrator_1_1407+284_L-Band_Std_ALL_0.fits    I29_17_1027+6812_L-Band_Std_ALL_0.fits
G29_9_1029+6812_L-Band_Std_ALL_0.fits          I31_15_1027+6817_L-Band_Std_ALL_0.fits
G31_11_1029+6817_L-Band_Std_ALL_0.fits         PCAL_3_1034+6832_L-Band_Std_ALL_0.fits
H28_7_1028+6809_L-Band_Std_ALL_0.fits
```

Also for this dataset a manual mask is needed to flag the slow start of the Lovell telescope in a file `manual.flags` which contains the line

```
mode='manual' field='' antenna='' timerange='18:30:00~18:40:00'
```

