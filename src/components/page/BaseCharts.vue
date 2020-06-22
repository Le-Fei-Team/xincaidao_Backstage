<template>
  <div>
    <div class="crumbs">
      <el-breadcrumb separator="/">
        <el-breadcrumb-item>
          <i class="el-icon-pie-chart"></i>产品统计分析
        </el-breadcrumb-item>
      </el-breadcrumb>
    </div>
    <div class="container">
      <div class="plugins-tips">
        <a href="https://github.com/lin-xin/vue-schart"
           target="_blank">产品分析图表</a>
      </div>
      <div class="schart-box">
        <div class="content-title">基金产品分析柱状图</div>
        <schart class="schart"
                canvasId="bar"
                :options="options1"></schart>
      </div>
      <div class="schart-box">
        <div class="content-title">证券类产品销售趋势图</div>
        <schart class="schart"
                canvasId="line"
                :options="options2"></schart>
      </div>
      <div class="schart-box">
        <div class="content-title">现金管理类销售饼状图</div>
        <schart class="schart"
                canvasId="pie"
                :options="options3"></schart>
      </div>
      <div class="schart-box">
        <div class="content-title">产品销售对比</div>
        <schart class="schart"
                canvasId="ring"
                :options="options4"></schart>
      </div>
    </div>
  </div>
</template>

<script>
import Schart from 'vue-schart';
export default {
  name: 'basecharts',
  components: {
    Schart
  },
  data() {
    return {
      options1: {
        type: 'bar',
        title: {
          text: '最近一周基金销售图'
        },
        bgColor: '#fbfbfb',
        labels: ['周一', '周二', '周三', '周四', '周五'],
        datasets: [
          {
            label: '安信基金',
            fillColor: 'rgba(241, 49, 74, 0.5)',
            data: [234, 278, 270, 190, 230]
          },
          {
            label: '汇安基金',
            data: [164, 178, 190, 135, 160]
          },
          {
            label: '红土创新基金',
            data: [144, 198, 150, 235, 120]
          }
        ]
      },
      options2: {
        type: 'line',
        title: {
          text: '近几月证券类产品销售趋势图'
        },
        bgColor: '#fbfbfb',
        labels: ['6月', '7月', '8月', '9月', '10月'],
        datasets: [
          {
            label: '长江证券',
            data: [234, 278, 270, 190, 230]
          },
          {
            label: '华融证券',
            data: [164, 178, 150, 135, 160]
          },
          {
            label: '国都证券',
            data: [114, 138, 200, 235, 190]
          }
        ]
      },
      options3: {
        type: 'pie',
        title: {
          text: '现金管理类销售饼状图'
        },
        legend: {
          position: 'left'
        },
        bgColor: '#fbfbfb',
        labels: ['国泰君安资产管理', '上海光大证券资产管理', '中泰证券(上海)资管', '浙商证券资管', '浙商证券资管'],
        datasets: [
          {
            data: [334, 278, 190, 235, 260]
          }
        ]
      },
      options4: {
        type: 'ring',
        title: {
          text: '产品销售对比'
        },
        showValue: false,
        legend: {
          position: 'bottom',
          bottom: 40
        },
        bgColor: '#fbfbfb',
        labels: ['基金类', '证券类', '现金管理类'],
        datasets: [
          {
            data: [600, 400, 500]
          }
        ]
      }
    };
  }
};
</script>

<style scoped>
.schart-box {
    display: inline-block;
    margin: 20px;
}
.schart {
    width: 600px;
    height: 400px;
}
.content-title {
    clear: both;
    font-weight: 400;
    line-height: 50px;
    margin: 10px 0;
    font-size: 22px;
    color: #1f2f3d;
}
</style>