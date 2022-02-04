I. Observations

We are obtaining photometry of the ULLYSES T Tauri stars with the automated [LCOGT](https://lco.global/) 0.4 m telescope network ([Brown et al. 2013](https://ui.adsabs.harvard.edu/abs/2013PASP..125.1031B/abstract)). For DR3, we are releasing photometry of the 13 survey stars in Orion that were observed with Hubble in November and December of 2020. Photometry of monitoring stars and additional survey stars will be included in future data releases.

The LCOGT 0.4 m network consists of ten telescopes at six observatories: Siding Spring Observatory (31º16' S, 149º4' E), South African Astronomical Observatory (32º23' S, 20º49' E), ‪Teide Observatory‬ (28º18' N, 16º31' W)‪,‬ Cerro Tololo Inter-American Observatory (30º10' S, 70º48' W), McDonald Observatory (30º40' N, 104º1' W), ‪and ‬Haleakala Observatory (20º42' N, 156º15' W). For the four monitoring stars, observations are made with the SDSS u' and i' filters and the Bessell V filter. For the survey stars, only the SDSS i' and Bessell V filters are used.

Observations are planned to occur 90 and 10 days before and after the Hubble observations. These four cadences each consist of daily observations over 10 day intervals. Observations are also planned to occur during a period that encompasses the Hubble observations. For monitoring stars, 30 observations are requested over the three consecutive rotation periods being monitored. For survey stars, 10 observations are requested over the rotation period during which the Hubble observations occur. Rotation periods were estimated from TESS data and supplied by Javier Serna (UNAM). Finally, observations are planned to occur every 15 minutes during Hubble observations.

There is not always a tight correspondence between the plans outlined above and the actual timing of observations. Weather or mechanical problems sometimes prevent observations from taking place, particularly the tightly constrained ones that are planned to run simultaneously with Hubble. In some cases, stars are not visible from any 0.4 m telescope during the Hubble observations. In this release, the observations scheduled for 90 days before the Hubble observations were spread over more than the nominal 10 days as we fine-tuned our observing plans. A star can have more observations than expected if its field was initially used for calibration (separate calibration fields ultimately proved to be unnecessary for V and i') or if it is within a few arcsec of another ULLYSES target.

In the event that Hubble observations fail and are rescheduled, additional LCOGT observations are scheduled to align with those. In the DR3 release, this was the case for V510 Ori, which was observed again in February 2021. The observations that would have been planned for 90 days after the rescheduled observations were actually constrained by the seasonal visibility of this star and instead occurred about six weeks after the rescheduled observations.

Exposure times were estimated assuming nominal sky conditions, but observations can occur through clouds that significantly reduce counts but are insufficient to automatically close the telescope. This can result in non-detections of the science targets (particularly the faintest ones) or in the detection of too few stars to determine an astrometric solution. Observations affected by these problems are not included in the photometry tables.

II. Photometry

Images reduced with the BANZAI pipeline ([‪McCully et al. 2018](https://ui.adsabs.harvard.edu/abs/2018SPIE10707E..0KM/abstract)) are available in the [LCOGT archive](https://archive.lco.global/). BANZAI performs bad-pixel masking, bias and dark removal, and flat-field correction. It also determines the astrometric solution and extracts a catalog of sources. We begin with the BANZAI-reduced images and determine an absolute flux calibration.

Our flux calibration is based on magnitudes cataloged by the [AAVSO Photometric All-Sky Survey](https://www.aavso.org/apass) (APASS, funded by the Robert Martin Ayers Sciences Fund and NSF AST-1412587). The pipeline is written in IDL. It first performs aperture photometry on sources in the BANZAI-generated catalog using aper.pro from the [IDL Astronomy User's Library](https://idlastro.gsfc.nasa.gov/) ([Landsman 1993](https://ui.adsabs.harvard.edu/abs/1993ASPC...52..246L/abstract)). It sums counts in a five-pixel radius and subtracts the modal signal in an annulus extending from 10 to 20 pixels. These sources are matched to sources in the APASS tables, using a matching radius of 2 arcsec. The relationship between APASS magnitudes and –2.5 times the logarithm of the LCOGT counts is fit with a line, ignoring three-sigma outliers. The slope of this line can vary to account for non-linearity in the instrument response; this term is typically very close to 1.

Next, we attempt to find a point source at the expected coordinates of the ULLYSES target. If a source is found, we perform aperture photometry using the same parameters described above. The measured counts are converted to a magnitude with the relationship determined above. We then convert this magnitude to a flux density using the zero-magnitude flux for the observed bandpass. Central wavelengths and zero-magnitude fluxes come from [Bessell et al. (1998)](https://ui.adsabs.harvard.edu/abs/1998A%26A...333..231B/abstract) for the Bessell V filter and from [Fukugita et al. (1996)](https://ui.adsabs.harvard.edu/abs/1996AJ....111.1748F/abstract) for the SDSS i' filter. The uncertainty is assumed to be dominated by the uncertainty in the measured counts of the ULLYSES target. Measurements with uncertainties greater than 20% of the fluxes (S/N < 5) are excluded from the photometry tables.

The output photometry files contain one line for each image analyzed. Each line contains the name of the LCOGT image file used for photometry, the MJD at the start and end of the observation, the central wavelength of the bandpass in Å, and the flux density and its uncertainty in ergs/s/cm<sup>2</sup>/Å. The MJD are stated with enough precision such that their difference gives the exposure time accurate to 1 ms. There is one file for each star that contains all images analyzed for all filters.