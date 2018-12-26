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
      :tooltip-template="'$#: value.from # - $#: value.to #'"
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
        type: 'rangeColumn',
        name: 'High and Low',
        fromField: 'low',
        toField: 'high'
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


