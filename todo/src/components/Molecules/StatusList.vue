<template>
  <div>
    <input
      type="radio"
      value="すべて"
      v-model="currentStatus"
      @change="changeStatus()"
      checked
    />すべて
    <input
      type="radio"
      value="作業中"
      v-model="currentStatus"
      @change="changeStatus()"
    />作業中
    <input
      type="radio"
      value="完了"
      v-model="currentStatus"
      @change="changeStatus()"
    />完了
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentStatus: 'すべて',
      statusList: ['すべて', '作業中', '完了'],
    };
  },
  methods: {
    changeStatus() {
      this.$emit('chengeStatus', this.currentStatus);
    },
  },
  created() {
    this.changeStatus();
  },
};
</script>
