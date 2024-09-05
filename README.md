<VegaLite
  spec={{
    "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
    "data": {
      "URL": "",
      "format": {"type": "csv"}
    },
    "mark": {
      "type": "line"
    },
    "encoding": {
      "x": {
        "field": "Year",
        "type": "ordinal"
      },
      "y": {
        "field": "Mean",
        "type": "quantitative"
      }
    }
  }}
/>
