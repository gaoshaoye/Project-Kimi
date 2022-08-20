<template>
<div class="common-layout">
    <el-container>
      <el-header>
        <div class="Kimi-header">
          <div class="Kimi-header__l">Project Kimi</div>
          <div class="Kimi-header__r">Order Progress Indicator</div>
        </div>
      </el-header>
      <el-main>
        <div class="home">        
          <div class="card-container">
            <el-card class="box-card" v-for="(order,i) in orders" :key="i">
              <ProgressDashboard
                          :green="order.orderG"
                          :yellow="order.orderY"
                          :red="order.orderR"
                          text="Processed Orders"
                        />
              <div class="legends">
                <div class="card-legend">
                  <div class="legend-dot dot-green"></div>
                  <div>New: </div>
                  <div>{{ order.orderG }}</div>
                </div>
                <div class="card-legend">
                  <div class="legend-dot dot-yellow"></div>
                  <div>Processing: </div>
                  <div>{{ order.orderY }}</div>
                </div>
                <div class="card-legend">
                  <div class="legend-dot dot-red"></div>
                  <div>Completed: </div>
                  <div>{{ order.orderR }}</div>
                </div>
              </div>
              
            </el-card>
          </div>
        </div>
      </el-main>
    </el-container>
  </div>
  

</template>

<script lang="ts">
import { defineComponent } from "vue";
import ProgressDashboard from "../components/ProgressDashboard.vue";
export default defineComponent({
  components: {
    ProgressDashboard,
  },
  computed: {},
  methods: {},
  data() {
    return {
      orders: [
        {
          orderG: 1,
          orderY: 1,
          orderR: 8,
        },
        {
          orderG: 0,
          orderY: 0,
          orderR: 0,
        },
        {
          orderG: 2,
          orderY: 5,
          orderR: 8,
        },
        {
          orderG: 0,
          orderY: 0,
          orderR: 8,
        },
        {
          orderG: 2,
          orderY: 0,
          orderR: 0,
        },
        {
          orderG: 0,
          orderY: 5,
          orderR: 0,
        }
      ]
        
      
    };
  },
});
</script>
<style lang="scss" scoped>
.home {
  width: 100%;
  min-height: 760px;
  background-color: #f2f3f5;
}

.dashboard-box {
  border: 2px solid #000000;
  display: flex;
  justify-content: center;
  align-items: center;
  width: auto;
  
}
.box-card {
  width: 300px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 25px 30px;
  
}
.card-container {
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
  display: flex;
  flex-wrap: wrap;
}
.Kimi-header {
  background-color: #fafafa;
  // height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 25px;
  &__l{
    height: 40px;
    font-size: 25px;
  }
  &__r{
    height: 40px; 
    font-size: 25px;
  }

}
.el-header,.el-main{
  padding: 0px !important;
}
.card-legend {
  font-size: 15px;
  display: flex;
  justify-content: space-between;
}
.legend-dot {
  border-radius: 50%;
  height: 0px;
  width: 0px;
  margin-top: auto;
  margin-bottom: auto;
}
.dot {
  &-green {
    border: 4px solid #8bc24a;
  }
  &-yellow {
    border: 4px solid #fdc60b;
  }
  &-red {
    border: 4px solid #fd5621;
  }
}
.legends {
  width: 130px;
  margin-left: auto;
  margin-right: auto;
}
</style>