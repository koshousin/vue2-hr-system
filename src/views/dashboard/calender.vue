<template>
  <el-calendar v-model="currentDate">
    <template 
      slot="dateCell"
      slot-scope="{date,data}">
      <div class="date-content">
        <span class="text">{{getDay(data.day)}}</span>
        <span class="rest" v-if="isWeekday(date)">休</span>
      </div>
    </template>
  </el-calendar>
</template>
<script>
  export default {
    data() {
      return {
        currentDate: new Date()
      }
    },
    methods:{
      getDay(value){
        const day = value.split('-')[2];
        //console.log(value);
        return day.startsWith('0') ? day.slice(1) : day;
      },
      isWeekday(date){
        const day = date.getDay();
        return day === 6 || day === 0;
      }
    }
  }
</script>
<style lang="scss" scoped>
  .select-box {
    display: flex;
    justify-content: flex-end;
  }

  ::v-deep .el-calendar-day {
    height:  auto;
  }
  ::v-deep .el-calendar-table__row td::v-deep .el-calendar-table tr td:first-child, ::v-deep .el-calendar-table__row td.prev{
    border:none;
  }
  .date-content {
    height: 40px;
    text-align: center;
    line-height: 40px;
    font-size: 14px;
  }
  .date-content .rest {
    color: #fff;
    border-radius: 50%;
    background: rgb(250, 124, 77);
    width: 20px;
    height: 20px;
    line-height: 20px;
    display: inline-block;
    font-size: 12px;
    margin-left: 10px;
  }
  .date-content .text{
    width: 20px;
    height: 20px;
    line-height: 20px;
    display: inline-block;
  }
  ::v-deep .el-calendar-table td.is-selected .text{
    background: #409eff;
    color: #fff;
    border-radius: 50%;
  }
  ::v-deep .el-calendar__header {
    display: none
  }
</style>
