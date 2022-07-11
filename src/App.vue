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

<template>
  <div
      class="card-img w-50 d-flex text-center flex-column my-0 mx-auto align-items-center container rounded pt-5 mt-5 pb-5  ">
    <div class="progress-box pt-5 text-center align-items-center">
      <CircleProgress
          :percent="number"
          :show-percent="false"
          :viewport="true"
          :border-width="10"
          :border-bg-width="10"
      />
      <span class="set-counter">{{ set }}</span>
      <div class="d-flex w-100 pb-5 justify-content-between flex-row-reverse align-items-center">
        <h1>26&deg</h1>
        <div>
          <figure>
            <img src="/image/icons8-abscissa-48.png" alt="#">
          </figure>
        </div>
      </div>
      <div>
        <figure>
          <img src="../public/gif/ecercise.gif" alt="gift" class="rounded" style="width: 179px;height: 139px;">
        </figure>
      </div>
    </div>
  </div>
</template>
<script>
import RadialProgressBar from "vue3-radial-progress";
import CircleProgress from "vue3-circle-progress";
import {ref, defineComponent, onMounted} from "vue";

export default {

  components: {
    RadialProgressBar,
    CircleProgress,
  },
  data: () => ({
    number: 0,
    set: 0
  }),
  methods: {
    setup() {
      const percent = ref(75);
      onMounted(() => {
        setInterval(() => {
          if (percent.value === 25) {
            percent.value++;
            console.log('plus')
          } else {
            percent.value = 0;
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
    counter() {
      setInterval((ej) => {
        //counter animation
        if (this.number !== 85 && this.set <= 5) {
          ej = this.number++;
        } else if (this.number >= -1 && this.set === 4) {
          this.number = 0
        } else {
          this.number = 0
        }
        // counter set
        if (this.number === 85) {
          // console.log(4)
          this.set++;
        }
      }, 100);


    },
    // setcounter(){
    //       setInterval(() =>{
    // },100)

    // }

  },
  mounted() {
    this.setup();
    this.counter(this.number);
    // this.setcounter()
  }
}
</script>


<style lang="scss">
body {

}

.card-img {
  padding: 0;
}

.set-counter {
  position: relative;
  top: -137px;
  font-size: 60px;
  font-weight: bold;

}

.progress-box {
  background: #66666691;
  padding: 35px;
  backdrop-filter: blur(70px);
  border-radius: 15px;
}
svg{
  stroke-dasharray: 457;
  transform: rotate(117deg) !important;
  stroke-linecap: round;
}
</style>