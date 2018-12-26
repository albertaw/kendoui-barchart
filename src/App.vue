<template>
  <div id="app">
    <kendo-datasource
      ref="dataSource"
      :transport-read-url="'https://api.iextrading.com/1.0/stock/amzn/chart'"
      :transport-read-data-type="'json'">
    </kendo-datasource>
    <kendo-chart
      :data-source-ref="'dataSource'"
      :title-text="'Amazon Stock Prices'"
      :legend-position="'bottom'"
      :tooltip-visible="true"
      :tooltip-template="'#: series.name #: $#: value #'"
      :theme="'material'"
      :series="series"
      :category-axis="categoryAxis"
      :value-axis="valueAxis">
    </kendo-chart>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      series: [{
        type: 'column',
        name: 'Low',
        field: 'low'
      },
      {
        type: 'column',
        name: 'High',
        field: 'high'
      }],
      categoryAxis: {
        field: 'label'
      },
      valueAxis: {
        labels: {
          format: '${0}'
        }
      }
    }
  }
}
</script>


<style>
#app {
  margin-top: 60px;
}
</style>


