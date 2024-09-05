<VegaLite
  spec={{
    $schema: 'https://vega.github.io/schema/vega-lite/v4.json',
    data: {
      URL: "data/co2-mm-gl.csv"
    },
    encoding: {
      x: {
        field: 'Date',
        type: 'temporal'
      },
      y: {
        field: 'Average',
        type: 'quantitative'
      }
    },
    mark: 'line'
  }}
/>
