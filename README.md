TEST

<VegaLite
  spec={{
    "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
    "data": {
      "url": "data/co2-annmean-mlo.csv"
    },
    "mark": {
      "type": "bar"
    },
    "encoding": {
      "x": {
        "field": "Year",
        "type": "nominal"
      },
      "y": {
        "field": "Mean",
        "type": "quantitative"
      }
    }
  }}
/>

