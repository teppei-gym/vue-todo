<template>
  <tr v-show="display">
    <td>{{ taskId }}</td>
    <td>{{ task }}</td>
    <td>
      <button @click="changeStatus()">{{ status }}</button>
    </td>
    <td>
      <button @click="deleteTask()">削除</button>
    </td>
  </tr>
</template>

<script>
export default {
  props: ['task', 'taskId', 'currentStatus'],
  data() {
    return {
      status: '作業中',
      display: true,
    };
  },
  methods: {
    changeStatus() {
      this.status = this.status === '作業中' ? '完了' : '作業中';
    },
    deleteTask() {
      this.$emit('deleteTask', this.task);
    },
    checkStatus() {
      if (this.currentStatus === 'すべて') {
        this.display = true;
      } else if (this.currentStatus === '作業中') {
        this.display = this.status === '作業中';
      } else if (this.currentStatus === '完了') {
        this.display = this.status === '完了';
      }
    },
  },
  watch: {
    currentStatus() {
      this.checkStatus();
    },
    status() {
      this.checkStatus();
    },
  },
  created() {
    this.checkStatus();
  },
};
</script>
