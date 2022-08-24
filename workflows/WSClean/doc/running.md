# Running

```
wsclean -j 8 -abs-mem 32 -name 1027+6812 -size 20000 20000 -scale 0.05asec -auto-mask 3 -auto-threshold 1.0 -niter 25000 -mgain 0.8 -weight natural 1027+6812.ms
```

Can view the map with ds9, casa viewer or CARTA (although it's not the most exciting field)
```
ds9 1027+6812-image.fits
```

