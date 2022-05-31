<template>
  <div class="father">
    <div class="content">
      <div class="dashboard-grey dashboard"></div>
      <div class="dashboard-red dashboard"></div>
      <div class="dashboard-yellow dashboard"></div>
      <div class="dashboard-green dashboard"></div>
      <div class="dashboard-white"></div>
      <div class="progress-orders-num">
        {{ $props.yellow + $props.red }}
      </div>
    </div>
    <div class="progress-orders-text">
      订单
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { ref } from "vue";
export default defineComponent({
  name: "ProgressDashboard",

  components: {},
  computed: {},
  methods: {},
  props: ["green", "yellow", "red"],
  setup(props, context) {
    const redAngle: any = ref(-90);
    const yellowAngle: any = ref(-90);
    const greenAngle: any = ref(-90);
    if (!(props.red == 0 && props.yellow == 0 && props.green == 0)) {
      redAngle.value =
        -90 +
        ((props.yellow + props.green + props.red) * 180) /
          (props.yellow + props.green + props.red);

      yellowAngle.value =
        -90 +
        ((props.yellow + props.green) * 180) /
          (props.yellow + props.green + props.red);
      greenAngle.value =
        -90 + (props.green * 180) / (props.yellow + props.green + props.red);
    }
    redAngle.value = redAngle.value + "deg";
    yellowAngle.value = yellowAngle.value + "deg";
    greenAngle.value = greenAngle.value + "deg";
    return { redAngle, yellowAngle, greenAngle };
  },
  data() {
    return {};
  },
});
</script>
<style lang="scss" scoped>
.father {
  height: 90px;
  width: 180px;
  overflow: hidden;
}
.content {
  overflow: hidden;
  height: 180px;
  width: 180px;
  position: absolute;
  z-index: 999;
  clip: rect(0px, 180px, 90px, 0px);
}
.dashboard {
  height: 180px;
  width: 180px;
  position: absolute;
  border-radius: 50%;
  clip: rect(0px, 90px, 180px, 0);
}
.dashboard-grey {
  background: #f3f3f3;
  transform: rotate(90deg);
}
.dashboard-red {
  background: #fd5621;
  transform: rotate(v-bind(redAngle));
}
.dashboard-yellow {
  background: #fdc60b;
  transform: rotate(v-bind(yellowAngle));
}
.dashboard-green {
  background: #8bc24a;
  transform: rotate(v-bind(greenAngle));
}
.dashboard-white {
  height: 164px;
  width: 164px;
  background: #ffffff;
  position: absolute;
  border-radius: 50%;
  clip: rect(0px, 82px, 164px, 0);
  transform: rotate(90deg);
  margin-left: 8px;
  margin-top: 8px;
  border-color: #ffffff;
}
.progress-orders-num {
  position: absolute;
  height: 33px;
  font-style: normal;
  font-weight: 500;
  font-size: 24px;
  line-height: 33px;
  letter-spacing: 1px;
  color: #333333;
  margin-top: 52px;
  margin-left: 75.65px;
}
.progress-orders-text {
  position: absolute;
  height: 16px;
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 16px;
  color: #333333;
  margin-top: 84px;
  margin-left: 60px;
  z-index: 9999;
}
</style>
