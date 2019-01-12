<template>
  <div class="ss-progress">
      <div class="ss-progress__wrapper">
          <div class="ss-progress-main">
              <div 
                class="ss-progress-main-line"
                :class="[
                  status && `${status}-bg`
                ]"
                :style="{ width: `${percentageMedium}%`}"
              >
              </div>
          </div> 
          <div 
            class="ss-progress-point"
            :class="[
              status && `icon-icon-status__${status}`,
              status && `${status}-text`
            ]"
          > 
          {{ status ?  '' : `${percentageMedium}%` }} 
          </div>
      </div>
    </div>
</template>

<script>
export default {
  props: {
    percentage: {
      type: Number,
      default: 0
    },

    status: {
      type: String,
      default: ''
    }
  },

  data() {
    return {
      percentageMedium: this.percentage,
      statusMedium: this.status
    }
  },

  watch: {
    percentage(n) {
      // eslint-disable-next-line
      this.percentageMedium = n >= 100 ? 
        this.setStatu() && 100 :
        n
    }
  },

  methods: {
    setStatu() {
      this.$emit('success');
      return true;
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/base.scss';
  .ss-progress {
    width: 100%;
    height: 20px;
    & > .ss-progress__wrapper {
      height: 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;

      & > .ss-progress-main {
        position: relative;
        width: 90%;
        height: 6px;
        background: #eee;
        &, & > div {
          border-radius: 3px;
        }
        & > .ss-progress-main-line {
          position: absolute;
          left: 0;
          top: 0;
          height: 100%;
          background: $mc;
          transition: all .3s linear;
        }

        & > .success-bg {
          background-color: $sc !important;
        }

        & > .error-bg {
          background-color: $ec !important;
        }
      }

      & > .ss-progress-point {
        width: 8%;
        line-height: 20px;
        font-size: 14px;
        color: #353535;
      }

      & > .success-text{
        color: $sc !important;
      }
      & > .error-text {
        color: $ec !important;
      }
    }
    
  }
</style>

