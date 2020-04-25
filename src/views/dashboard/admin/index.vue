<template>
  <div class="dashboard-editor-container">
    <!-- <github-corner class="github-corner" /> -->

    <panel-group @handleSetLineChartData="handleSetLineChartData" />

    <el-row style="background:#fff;padding:16px 16px 0;margin-bottom:32px;">
      <line-chart :chart-data="lineChartData" />
    </el-row>

    <el-row :gutter="32">
      <!-- <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <raddar-chart />
        </div>
      </el-col>-->
      <!-- <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <div class="title-container">
            <h3 class="title">ITV到达量</h3>
          </div>
          <pie-chart />
        </div>
      </el-col> -->
    
      <el-col :xs="24" :sm="24" :lg="12">
        <div class="chart-wrapper">
          <div class="title-container">
            <h3 class="title" >天翼看家到达量</h3>
          </div>
          <pie3 />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="12">
        <div class="chart-wrapper">
          <div class="title-container">
            <h3 class="title">智能组网到达量</h3>
          </div>
          <pie2 />
        </div>
      </el-col>
      <!-- <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <bar-chart />
        </div>
      </el-col>-->
    </el-row>

    <!-- <el-row :gutter="8">
      <el-col :xs="{span: 24}" :sm="{span: 24}" :md="{span: 24}" :lg="{span: 12}" :xl="{span: 12}" style="padding-right:8px;margin-bottom:30px;">
        <transaction-table />
      </el-col>
      <el-col :xs="{span: 24}" :sm="{span: 12}" :md="{span: 12}" :lg="{span: 6}" :xl="{span: 6}" style="margin-bottom:30px;">
        <todo-list />
      </el-col>
      <el-col :xs="{span: 24}" :sm="{span: 12}" :md="{span: 12}" :lg="{span: 6}" :xl="{span: 6}" style="margin-bottom:30px;">
        <box-card />
      </el-col>
    </el-row>-->
  </div>
</template>

<script>
import GithubCorner from '@/components/GithubCorner'
import PanelGroup from './components/PanelGroup'
import LineChart from './components/LineChart'
import RaddarChart from './components/RaddarChart'
import PieChart from './components/PieChart'
import pie2 from './components/pie2'
import pie3 from './components/pie3'

import BarChart from './components/BarChart'
import TransactionTable from './components/TransactionTable'
import TodoList from './components/TodoList'
import BoxCard from './components/BoxCard'

const lineChartData = {
  newVisitis: {
    // expectedData: [0, 4, 17, 26, 27, 27, 30, 32, 39, 43, 46, 51, 51],
    // actualData: [0, 0, 1, 4, 5, 1, 1, 0, 1, 1, 0, 0, 0],
    guichiquData: [0, 10, 35, 45, 48, 49, 54, 60, 79, 90, 91,95, 101],
    shitaiData: [0, 6, 25, 39, 47, 54, 60, 63,64, 83, 85, 86, 88],
    dongzhiData: [0, 13, 25, 36, 47, 62],
    jiuhuashanData: [0, 10, 18, 41, 50, 68]
  },
  messages: {
    // expectedData: [0, 0, 4, 22, 37, 45, 46, 49, 52, 67, 71, 81, 86],
    // actualData: [0, 0, 0, 3, 8, 9, 9, 10, 11, 12, 14, 15, 15],
    guichiquData: [0, 0, 1, 4, 12, 15, 15, 16, 18, 25, 26, 33, 37],
    shitaiData: [0, 0, 0, 0, 0, 1, 1, 1, 1, 4, 5, 5, 5],
    dongzhiData: [0, 0, 3, 15, 17, 18],
    jiuhuashanData: [0, 4, 5, 13, 22, 25]
  },
  purchases: {
    // expectedData: [0, 0, 8, 17, 23, 28, 33, 35, 48, 54, 61, 63, 63],
    // actualData: [0, 0, 2, 4, 1, 1, 2, 0, 1, 3, 1, 0, 0],
    guichiquData: [0, 4, 17, 26, 27, 27, 30, 32, 39, 43, 46, 51, 51],
    shitaiData: [0, 5, 11, 20, 32, 44, 60, 70, 77, 80, 85, 86, 88],
    dongzhiData: [0, 0, 3, 7, 11, 17],
    jiuhuashanData: [0, 2, 5, 10, 15, 22]
  },
  shoppings: {
    // expectedData: [0, 1, 12, 29, 38, 43, 50, 60, 79, 90, 100, 111, 111],
    // actualData: [0, 0, 4, 7, 3, 1, 1, 2, 4, 4, 2, 0, 0],
    guichiquData: [0, 0, 4, 22, 37, 45, 46, 49, 52, 67, 71, 81, 86],
    shitaiData: [0, 0, 0, 3, 8, 9, 9, 10, 11, 12, 14, 15, 15],
    dongzhiData: [0, 2, 5, 13, 16, 25],
    jiuhuashanData: [0, 3, 6, 16, 17, 21]
  }
}

export default {
  name: 'DashboardAdmin',
  components: {
    GithubCorner,
    PanelGroup,
    LineChart,
    RaddarChart,
    PieChart,
    
    pie2,
    pie3,
    BarChart,
    TransactionTable,
    TodoList,
    BoxCard
  },
  data() {
    return {
      lineChartData: lineChartData.newVisitis
    }
  },
  methods: {
    handleSetLineChartData(type) {
      this.lineChartData = lineChartData[type]
    }
  }
}
</script>

<style lang="scss" scoped>
.title-container {
  position: relative;

  .title {
    font-size: 26px;
    color: blue;
    margin: 0px auto 40px auto;
    text-align: center;
    font-weight: bold;
  }
}

.dashboard-editor-container {
  padding: 32px;
  background-color: rgb(240, 242, 245);
  position: relative;

  .github-corner {
    position: absolute;
    top: 0px;
    border: 0;
    right: 0;
  }

  .chart-wrapper {
    background: #fff;
    padding: 16px 16px 0;
    margin-bottom: 32px;
  }
}

@media (max-width: 1024px) {
  .chart-wrapper {
    padding: 8px;
  }
}
</style>
