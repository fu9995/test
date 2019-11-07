<template>
  <div class="home">
    <el-checkbox
      :indeterminate="isIndeterminate1"
      v-model="checkAll1"
      @change="handleCheckAllChange1"
      class="title"
    >星期一</el-checkbox>
    <el-checkbox-group class="list" v-model="checkedCities1" @change="handleCheckedCitiesChange1">
      <el-checkbox v-for="city1 in cities1" :label="city1" :key="city1">{{city1}}</el-checkbox>
    </el-checkbox-group>
    <el-checkbox
      :indeterminate="isIndeterminate2"
      v-model="checkAll2"
      @change="handleCheckAllChange2"
      class="title"
    >星期二</el-checkbox>
    <el-checkbox-group class="list" v-model="checkedCities2" @change="handleCheckedCitiesChange2">
      <el-checkbox v-for="city2 in cities2" :label="city2" :key="city2">{{city2}}</el-checkbox>
    </el-checkbox-group>
  </div>
</template>
<script>
const cityOptions = ["1", "2", "3", "4","5"];
export default {
  data() {
    return {
      checkAll1: false,
      checkedCities1: [],
      cities1: cityOptions,
      isIndeterminate1: false,
      checkAll2: false,
      checkedCities2: [],
      cities2: cityOptions,
      isIndeterminate2: false
    };
  },
  methods: {
    handleCheckAllChange1(val1) {
      this.checkedCities1 = val1 ? cityOptions : [];
      this.isIndeterminate1 = false;
    },
    handleCheckedCitiesChange1(value1) {
      let checkedCount1 = value1.length;
      this.checkAll1 = checkedCount1 === this.cities1.length;
      this.isIndeterminate1 =
        checkedCount1 > 0 && checkedCount1 < this.cities1.length;
    },
    handleCheckAllChange2(val2) {
      this.checkedCities2 = val2 ? cityOptions : [];
      this.isIndeterminate2 = false;
    },
    handleCheckedCitiesChange2(value2) {
      let checkedCount2 = value2.length;
      this.checkAll2 = checkedCount2 === this.cities2.length;
      this.isIndeterminate2 =
        checkedCount2 > 0 && checkedCount2 < this.cities2.length;
    }
  }
};
</script>
<style>
.home{
  width:100%;
  height:100%;
}
.title,.list{
  display: inline-block;
}
.title{
  width:100px;
  height:30px;
  line-height: 30px;
}
.list{
  width:300px;
  height:30px;
  line-height: 30px;
  float: right;
}
</style>