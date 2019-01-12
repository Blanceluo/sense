<template>
  <div>
    <ss-progress 
    :percentage="num"
    :status="status"
    @success="status = 'success'"
    >
    </ss-progress>
  </div>
</template>
<script>
import ssProgress from '../components/progress/index';

export default {
  components: {
    ssProgress
  },

  data() {
    return {
      num: 0,
      status: ''
    }
  },

  created() {
    this.test();
  },

  methods: {
    test() {
      setInterval(() => {
        this.num = this.num + 1;
      }, 100);
    },

    setSuccess() {
      // this.status = 'success';
    }
  }
}
</script>

<style lang="scss" scoped>
  div {
    width: 500px;
  }
</style>


