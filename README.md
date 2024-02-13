---
datapackage:
  name: co2-ppm
  title: "CO2 PPM - Trends in Atmospheric Carbon Dioxide"
  description: "Data are sourced from the US Government's Earth System Research Laboratory, Global Monitoring Division. Two main series are provided: the Mauna Loa series (which has the longest continuous series since 1958) and a Global Average series (a global average over marine surface sites)."
  homepage: http://www.esrl.noaa.gov/gmd/ccgg/trends
  version: 0.1.0
  licenses:
    - name: ODC-PDDL-1.0
      path: http://opendatacommons.org/licenses/pddl/
      title: Open Data Commons Public Domain Dedication and License v1.0
  sources:
    - name: Trends in Atmospheric Carbon Dioxide, Mauna Loa, Hawaii
      path: http://www.esrl.noaa.gov/gmd/ccgg/trends/index.html
      title: Trends in Atmospheric Carbon Dioxide, Mauna Loa, Hawaii
    - name: Trends in Atmospheric Carbon Dioxide, Global
      path: http://www.esrl.noaa.gov/gmd/ccgg/trends/global.html
      title: Trends in Atmospheric Carbon Dioxide, Global
  resources:
    - name: co2-mm-mlo
      path: data/co2-mm-mlo.csv
      format: csv
      mediatype: text/csv
      schema:
        fields:
          - name: Date
            type: date
            description: YYYY-MM-DD
            format: any
          - name: Decimal Date
            type: number
            description: ""
          - name: Average
            type: number
            description: The monthly mean CO2 mole fraction determined from daily averages. If there are missing days concentrated either early or late in the month, the monthly mean is corrected to the middle of the month using the average seasonal cycle. Missing months are denoted by -99.99.
          - name: Interpolated
            type: number
            description: Values from the average column and interpolated values where data are missing. Interpolated values are computed in two steps. First, we compute for each month the average seasonal cycle in a 7-year window around each monthly value. In this way the seasonal cycle is allowed to change slowly over time. We then determine the trend value for each month by removing the seasonal cycle; this result is shown in the trend column. Trend values are linearly interpolated for missing months. The interpolated monthly mean is then the sum of the average seasonal cycle value and the trend value for the missing month.
          - name: Trend
            type: number
            description: Seasonally corrected.
          - name: Number of Days
            type: number
            description: -1 denotes no data for number of daily averages in the month.
    - name: co2-annmean-mlo
      path: data/co2-annmean-mlo.csv
      format: csv
      mediatype: text/csv
      schema:
        fields:
          - name: Year
            type: date
            description: ""
            format: any
          - name: Mean
            type: number
            description: ""
          - name: Uncertainty
            type: number
            description: The estimated uncertainty in the annual mean is the standard deviation of the differences of annual mean values determined independently by NOAA/ESRL and the Scripps Institution of Oceanography.
    - name: co2-gr-mlo
      path: data/co2-gr-mlo.csv
      format: csv
      mediatype: text/csv
      schema:
        fields:
          - name: Year
            type: date
            description: ""
            format: any
          - name: Annual Increase
            type: number
            description: Annual CO2 mole fraction increase (ppm) from Jan 1 through Dec 31.
          - name: Uncertainty
            type: number
            description: Estimated from the standard deviation of the differences between monthly mean values determined independently by the Scripps Institution of Oceanography and by NOAA/ESRL.
    - name: co2-mm-gl
      path: data/co2-mm-gl.csv
      format: csv
      mediatype: text/csv
      schema:
        fields:
          - name: Date
            type: date
            description: YYYY-MM-DD
            format: any
          - name: Decimal Date
            type: number
            description: ""
          - name: Average
            type: number
            description: ""
          - name: Trend
            type: number
            description: ""
    - name: co2-annmean-gl
      path: data/co2-annmean-gl.csv
      format: csv
      mediatype: text/csv
      schema:
        fields:
          - name: Year
            type: date
            description: ""
            format: any
          - name: Mean
            type: number
            description: ""
          - name: Uncertainty
            type: number
            description: The uncertainty in the global annual mean is estimated using a monte carlo technique that computes 100 global annual averages, each time using a slightly different set of measurement records from the NOAA ESRL cooperative air sampling network.  The reported uncertainty is the mean of the standard deviations for each annual average using this technique. Please see Conway et al., 1994, JGR, vol. 99, no. D11. for a complete discussion.
    - name: co2-gr-gl
      path: data/co2-gr-gl.csv
      format: csv
      mediatype: text/csv
      schema:
        fields:
          - name: Year
            type: date
            description: ""
            format: any
          - name: Annual Increase
            type: number
            description: Annual CO2 mole fraction increase (ppm) from Jan 1 through Dec 31.
          - name: Uncertainty
            type: number
            description: The uncertainty in the global annual mean growth rate is estimated using a monte carlo technique that computes 100 time series of global annual growth rates, each time using measurement records from a different sampling of sites from the NOAA ESRL cooperative air sampling network. Each year has a different uncertainty. Please see Conway et al., 1994, JGR, vol. 99, no. D11. for a complete discussion. The last one or two years listed could have preliminary uncertainties set equal to the average uncertainty since 1980. Before 1980 the global growth rate has been approximated by taking the average of Mauna Loa and the South Pole, correcting for the offset between (MLO+SPO)/2 and the global Marine Boundary Layer, as described in Ballantyne et al, 2012.
  views:
    - name: graph
      title: Trends in Atmospheric Carbon Dioxide
      resources: ["co2-mm-mlo"]
      specType: simple
      spec:
        type: lines-and-points
        group: Date
        series:
          - Interpolated
          - Trend
    - name: growth-rate
      title: Growth rate of Carbon Dioxide
      resources: ["co2-gr-mlo"]
      specType: simple
      spec:
        type: bar
        group: Year
        series:
          - Annual Increase

---

CO2 PPM - Trends in Atmospheric Carbon Dioxide. Data are sourced from the US Government's Earth System Research Laboratory, Global Monitoring Division. Two main series are provided: the Mauna Loa series (which has the longest continuous series since 1958) and a Global Average series (a global average over marine surface sites).

## Data

### Description

> Data are reported as a dry air mole fraction defined as the number of molecules of carbon dioxide divided by the number of all molecules in air, including CO2 itself, after water vapor has been removed. The mole fraction is expressed as parts per million (ppm). Example: 0.000400 is expressed as 400 ppm.[*][ccgg-trends]

### Citations

1. *Trends in Atmospheric Carbon Dioxide, Mauna Loa, Hawaii.* Dr. Pieter Tans, NOAA/ESRL (www.esrl.noaa.gov/gmd/ccgg/trends/) and Dr. Ralph Keeling, Scripps Institution of Oceanography (scrippsco2.ucsd.edu/).
1. *Trends in Atmospheric Carbon Dioxide, Global.* Ed Dlugokencky and Pieter Tans, NOAA/ESRL (www.esrl.noaa.gov/gmd/ccgg/trends/).

### Sources

1. 
  * Name: Trends in Atmospheric Carbon Dioxide, Mauna Loa, Hawaii
  * Web: http://www.esrl.noaa.gov/gmd/ccgg/trends/index.html
1. 
  * Name: Trends in Atmospheric Carbon Dioxide, Global
  * Web: http://www.esrl.noaa.gov/gmd/ccgg/trends/global.html

## Preparation

### Processing

Run the following script from this directory to download and process the data:

```bash
./scripts/process.sh
```

Most likely works for Unix systems only. (Not Windows compatible)

### Resources

The raw data is output to `./tmp`. (Not committed to the repository, you'll have to clone and run locally) The processed data is output to `./data`.

## License

### ODC-PDDL-1.0

This Data Package is made available under the Public Domain Dedication and License v1.0 whose full text can be found at: http://www.opendatacommons.org/licenses/pddl/1.0/

### Notes

The [terms of use][gmd] of the source dataset list three specific restrictions on public use of these data:

> The information on government servers are in the public domain, unless specifically annotated otherwise, and may be used freely by the public so long as you do not 1) claim it is your own (e.g. by claiming copyright for NOAA information – see next paragraph), 2) use it in a manner that implies an endorsement or affiliation with NOAA, or 3) modify it in content and then present it as official government material.[*][gmd]

[ccgg-trends]: http://www.esrl.noaa.gov/gmd/ccgg/trends/index.html
[gmd]: http://www.esrl.noaa.gov/gmd/about/disclaimer.html
