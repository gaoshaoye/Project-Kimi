<template>
  <div class="home">
   <div class="dashboard-box">
    <ProgressDashboard
                :green="orderG"
                :yellow="orderY"
                :red="orderR"
              />
   </div>
   <div>测试</div>
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
      orderG: 1,
      orderY: 1,
      orderR: 8,
    };
  },
});
</script>
<style lang="scss" scoped>
.home {
  width: 100%;
}
.dashboard-box {
  border: 2px solid #000000;
  display: flex;
  justify-content: center;
  align-items: center;
  width: auto;
}
</style>