TEST

<VegaLite
  data={{
    URL: "data/co2-annmean-mlo.csv"
  }}
  spec={{
    $schema: 'https://vega.github.io/schema/vega-lite/v4.json',
    data: {
      name: 'table'
    },
    encoding: {
      x: {
        field: 'Year',
        type: 'temporal'
      },
      y: {
        field: 'Mean',
        type: 'quantitative'
      }
    },
    mark: 'line'
  }}
/>
