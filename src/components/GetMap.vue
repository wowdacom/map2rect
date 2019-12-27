<template>
  <div class="getMap">
    <ul :key="indexColumn + 'column'" v-for="(item, indexColumn) in record">
      <li @click="handleDraw(indexColumn, indexRow)" class="box" :class="{ active: record[indexColumn][indexRow] }" :key="indexRow + 'column'" v-for="(item, indexRow) in  record[indexColumn]"></li>
    </ul>
    <div @click="getMap" class="output">輸出圖片</div>
    <select v-model="selected">
      <option disabled value="">Please select one</option>
      <option :key="item" v-for="item in currentCity">{{ item }}</option>
    </select>
    <span>Selected: {{ selected }}</span>
  </div>
</template>

<script>
export default {
  name: 'getMap',
  data (){
    return {
      record: [
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false],
        [false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false,false]
      ],
      selected: '',
      result: [],
      currentCity: ["臺北市","新北市","基隆市","桃園市","新竹縣","新竹市","苗栗縣","臺中市","南投縣","彰化縣","雲林縣","嘉義縣","嘉義市","臺南市","高雄市","屏東縣","花蓮縣","臺東縣","宜蘭縣","連江縣","金門縣","澎湖縣"]
    }
  },
  props: {
    msg: String
  },
  mounted () {
    // this.record = new Array(15)
    // this.record.forEach((item)=>{
    //   item = new Array(30)
    //   item.fill(false, 0, 30)
    // })

  },
  methods: {
    handleDraw (column, row) {
      let vm =this
      let city = vm.selected
      if (this.record[column][row] === false) {
        this.$set(this.record[column], row, true)
        let newdata = new Object();
        newdata[city] = {'x': column,'y': row}
        this.result.push(newdata)
      } else {
         this.$set(this.record[column], row, false)
      }
      console.log(column, row)
      // console.log(this.record[column][row])
    },
    getMap () {
      let vm = this
      // this.record.forEach((item, indexColoomne)=>{
      //   item.forEach((itemInner, indexRow)=>{
      //     if (itemInner === true) {
      //       vm.result.push({'x': indexColoomne, 'y':indexRow })
      //     }
      //   })
      // })
      console.log(this.result)
    }
  },
  watch: {
    record: {
      handler(newName, oldName) {
        console.log(newName);
      },
      deep: true
    }
  } 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.getMap {
  display: flex;
  justify-content: center;
  align-items: center;
    ul {
      list-style: none;
      margin: 0;
      padding: 0;
        .box {
            height: 15px;
            width: 15px;
            border: solid 1px black;
            margin: 0;
            &.active {
              background-color: green;
            }
        }
    }
    .output {
      background-color: pink;
      padding: 5px;
      border-radius: 5px;
      color: gray;
    }
}
</style>
