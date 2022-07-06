<template>
<!--  <div class="container">-->
<!--    <div class="my-0 mx-auto border-info">-->
<!--      <div class="d-flex flex-column">-->
<!--&lt;!&ndash;progres&ndash;&gt;-->
<!--        <div class="progresss">-->
<!--          <radial-progress-bar-->
<!--              :diameter="500"-->
<!--              :completed-steps="100"-->
<!--              :total-steps="finallProgs">-->
<!--            &lt;!&ndash; Your inner content here &ndash;&gt;-->
<!--          </radial-progress-bar>-->
<!--        </div>-->
<!--&lt;!&ndash;deg&ndash;&gt;-->
<!--        <div class="flex justify-content-between">-->
<!--          <span></span>-->
<!--          <span></span>-->
<!--        </div>-->
<!--&lt;!&ndash;gif&ndash;&gt;-->
<!--        <div>-->

<!--        </div>-->
<!--      </div>-->
<!--    </div>-->
<!--  </div>-->

    <CircleProgress
        :percent="1"
        :viewport="true"
        :show-percent="true"
        :is-gradient="true"
    />
  </template>




<script>
import RadialProgressBar from "vue3-radial-progress";
import CircleProgress from "vue3-circle-progress";
import "vue3-circle-progress/dist/circle-progress.css";
import { ref, defineComponent , onMounted } from "vue";
export default {

components:{
  RadialProgressBar,
  CircleProgress,
},
  data: () => ({
    // finallProgs:15
  }),
methods:{
  setup() {
    const percent = ref(75);

    onMounted(() => {
      setInterval(() => {
        if (percent.value === 25) {
          percent.value = 75;
        } else {
          percent.value = 25;
        }
      }, 1000);
    });

    return {
      percent,
    };
  },
  // setup(){
  //   const completedSteps = ref(0);
  //   const totalSteps = ref(10);
  //
  //   return {
  //     completedSteps,
  //     totalSteps
  //   }
  // },
},
  mounted() {
  this.setup();
  }
}
</script>


<style lang="scss">
body * {
  background-color: orange;
}
</style>