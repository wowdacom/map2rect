<template>
  <div class="hello">
    <div id="world"></div>
  </div>
</template>

<script>
import * as topojson from 'topojson-client';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted () {

    let config = {
      width : 700,
      height : 700,
      padding : 10,
      projection : d3.geoMercator(),
      duration : 3000,
      key:function(d){
        return d.properties.COUNTYNAME;
      },
      grid: {
        "臺北市": {
          x: 4,
          y: 2
        },
        "新北市": {
          x: 5,
          y: 3
        },
        "基隆市": {
          x: 5,
          y: 2
        },
        "桃園市": {
          x: 4,
          y: 4
        },
        "新竹縣": {
          x: 4,
          y: 5
        },
        "新竹市": {
          x: 4,
          y: 3
        },
        "苗栗縣": {
          x: 3,
          y: 4
        },
        "臺中市": {
          x: 3,
          y: 5
        },
        "南投縣": {
          x: 3,
          y: 6
        },
        "彰化縣": {
          x: 2,
          y: 5
        },
        "雲林縣": {
          x: 2,
          y: 6
        },
        "嘉義縣": {
          x: 3,
          y: 7
        },
        "嘉義市": {
          x: 2,
          y: 7
        },
        "臺南市": {
          x: 2,
          y: 8
        },
        "高雄市": {
          x: 3,
          y: 8
        },
        "屏東縣": {
          x: 3,
          y: 9
        },
        "花蓮縣": {
          x: 4,
          y: 6
        },
        "臺東縣": {
          x: 4,
          y: 7
        },
        "宜蘭縣": {
          x: 5,
          y: 4
        },
        "連江縣": {
          x: 2,
          y: 0
        },
        "金門縣": {
          x: 0,
          y: 3
        },
        "澎湖縣": {
          x: 0,
          y: 7
        }
      }
    };

    let svg = d3.select('#world').append('svg').attr('width',config.width).attr('height',config.height);

    let g2r = new geo2rect.draw();
    d3.json('./json/tw_moi.json', function(err, data){

      let feature = topojson.feature(data, data.objects["COUNTY_MOI_1081121"]);
      var geojson = geo2rect.compute(feature);
      g2r.config = config;
      g2r.data = geojson;
      g2r.svg = svg.append('g');
      g2r.draw();
      setTimeout(function(){
         g2r.toggle();
         g2r.draw();
      }, 3000)

      console.log(g2r.mode);
    });

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
