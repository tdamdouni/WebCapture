# Global Sea Ice

_Captured: 2017-05-02 at 00:20 from [sites.google.com](https://sites.google.com/site/arctischepinguin/home/global-sea-ice)_

Welcome to this page with some graphics of global sea ice. Global means that northern and southern hemispheres are combined. Most of them will be updated daily as the source data for them is updated.

I did create these graphs when I getting myself familiar with a new (for me) graphic package ([Matplotlib](http://matplotlib.org/)) and choose to generate some similar to those from [The Cryosphere Today](http://arctic.atmos.uiuc.edu/cryosphere/). This site has stopped updating its data since spring 2016 and was the only source (know to me) that provided near real time sea ice area data or global sea ice coverage data (extent or area).

_  
Area_ is calculated from NSIDC sea ice concentration data (see below). It is the total measured sea ice covered area in grid cells with average sea ice concentration greater or equal to 15%. The ice concentration near the North Pole that can not be measured due to the satellite orbit (the so called "pole hole") is estimated from the surrounding sea ice. The pole hole calculation is similar to that used by the now defunct site [The Cryosphere Today](http://arctic.atmos.uiuc.edu/cryosphere/) although other details are different. Area calculated by NSIDC does not include the pole hole area in its area figures; because the pole hole area is different for the generations of satellites the resulting area cannot be used for year to year comparisons.  
_  
Extent_ is calculated from NSIDC sea ice concentration data (see below). It is the total area of grid cells with average sea ice concentration greater or equal to 15%. The ice concentration near the North Pole that can not be measured due to the satellite orbit (the so called "pole hole") is assed to be greater than 15%. The calculation is identical to the one employed by NSIDC and the daily results are identical too (no surprise).

_Sea Ice Concentration_ is "[NSIDC Sea Ice Concentrations from Nimbus-7 SMMR and DMSP SSM/I-SSMIS Passive Microwave Data (NSIDC-0051)](http://nsidc.org/data/nsidc-0051.html)" and for the most recent (about 1 year) data "[NSIDC Near-Real-Time DMSP SSMIS Daily Polar Gridded Sea Ice Concentrations](http://nsidc.org/data/nsidc-0081.html) ".

References: Cavalieri, D. J., C. L. Parkinson, P. Gloersen, and H. J. Zwally. 1996, updated yearly. _Sea Ice Concentrations from Nimbus-7 SMMR and DMSP SSM/I-SSMIS Passive Microwave Data, Version 1_. Boulder, Colorado USA. NASA National Snow and Ice Data Center Distributed Active Archive Center. doi: <http://dx.doi.org/10.5067/8GQ8LZQVL0VL>.  
Maslanik, J. and J. Stroeve. 1999, updated daily. _Near-Real-Time DMSP SSMIS Daily Polar Gridded Sea Ice Concentrations, Version 1_. Boulder, Colorado USA. NASA National Snow and Ice Data Center Distributed Active Archive Center. doi: <http://dx.doi.org/10.5067/U8C09DWVX9LM>.

_  
Volume_ is calculated from GIOMAS ( Global Ice-Ocean Modeling and Assimilation System) sea ice thickness. There are more graphics based on GIOMAS on [the giomas page](https://sites.google.com/site/arctischepinguin/home/giomas).  
Reference: Zhang, Jinlun and D.A. Rothrock: [Modeling global sea ice with a thickness and enthalpy distribution model in generalized curvilinear coordinates](http://psc.apl.washington.edu/zhang/Pubs/POIM.pdf), Mon. Wea. Rev. 131(5), 681-697, 2003  
Here is the [description](http://psc.apl.washington.edu/zhang/Global_seaice/model.html) , here is the [data](http://psc.apl.washington.edu/zhang/Global_seaice/).

_Data:_ daily values of global sea ice area, extent including anomalies and standard deviations are in [this daily updated zipped text file](https://sites.google.com/site/arctischepinguin/home/sea-ice-extent-area/data/nsidc_global_nt_final_and_nrt.txt.gz?attredirects=0).  
Monthly GIOMAS volume data are in [this text file.](https://sites.google.com/site/arctischepinguin/home/giomas/data/giomas-sumdata.csv.txt?attredirects=0)

Note: the grey area is the average sea ice area for the day of year +/- two standard deviations (+/- 2σ). Average and standard deviation are computed from the 1981-2010 (WMO standard) data.  
  
Permanent address: https://sites.google.com/site/arctischepinguin/home/sea-ice-extent-area/grf/nsidc_global_area_byyear_b.png
![](https://sites.google.com/site/arctischepinguin/_/rsrc/1493639462973/home/sea-ice-extent-area/grf/nsidc_global_area_byyear_b.png?height=300&width=400)

Note: the grey area is the average sea ice extent for the day of year +/- two standard deviations (+/- 2σ). Average and standard deviation are computed from the 1981-2010 (WMO standard) data.  
  
Permanent address: https://sites.google.com/site/arctischepinguin/home/sea-ice-extent-area/grf/nsidc_global_extent_byyear_b.png
![](https://sites.google.com/site/arctischepinguin/_/rsrc/1493639473545/home/sea-ice-extent-area/grf/nsidc_global_extent_byyear_b.png?height=300&width=400)

Normalized anomaly (anomaly divided by the standard deviation) shows the departure from normal in "sigma's", or "σ". One should expect the value to be between -2σ and +2σ about 95% of the time for a pure random signal with a normal distribution. Eight sigma's is more something for fundamental particle physics.  
  
  
  
Permanent address: https://sites.google.com/site/arctischepinguin/home/sea-ice-extent-area/grf/nsidc_global_area_normanomaly.png  

![](https://sites.google.com/site/arctischepinguin/_/rsrc/1493639480623/home/sea-ice-extent-area/grf/nsidc_global_area_normanomaly.png?height=100&width=400)

Normalized anomaly (anomaly divided by the standard deviation) shows the departure from normal in "sigma's", or "σ". One should expect the value to be between -2σ and +2σ about 95% of the time for a pure random signal with a normal distribution.  
  
  
  
Permanent address: https://sites.google.com/site/arctischepinguin/home/sea-ice-extent-area/grf/nsidc_global_extent_normanomaly.png

The "long" graphic of global sea ice extent; actual, normal and anomaly values. The second peak of the double maximum is nearly absent in 2016.  
  
Permanent address: https://sites.google.com/site/arctischepinguin/home/sea-ice-extent-area/grf/nsidc_global_extent.png

Volume tells a similar story. Color coding is different because I used an older graphic package. Years 1979-201 are represented by grey lines.  
  
  
Permanent address: https://sites.google.com/site/arctischepinguin/home/giomas/grf/giomas-year-GLOBAL.png
![](https://sites.google.com/site/arctischepinguin/_/rsrc/1483610063766/home/giomas/grf/giomas-year-GLOBAL.png?height=300&width=400)

The anomaly graph, with a linear regression, tells that the drop in volume actually started in 2015 high above the trend line to far below in a bit over a year.  
  
  
  
Permanent address: https://sites.google.com/site/arctischepinguin/home/giomas/grf/giomas-anomaly-all-GLOBAL.png
![](https://sites.google.com/site/arctischepinguin/_/rsrc/1483545127989/home/giomas/grf/giomas-anomaly-all-GLOBAL.png?height=300&width=400)
