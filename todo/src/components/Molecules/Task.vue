<template>
  <div>
    <table>
      <thead>
        <tr>
          <th>id</th>
          <th>コメント</th>
          <th>状態</th>
        </tr>
      </thead>
      <tbody id="tbody">
        <Tr
          v-for="(val, index) in tasks"
          :key="val + index"
          :task="val"
          :taskId="index + 1"
          :currentStatus="currentStatus"
          @deleteTask="deleteTask($event)"
        ></Tr>
      </tbody>
    </table>
    <div>
      <h2>新規タスク追加</h2>
      <input type="text" v-model="task" />
      <button @click="addTask">追加</button>
    </div>
  </div>
</template>

<script>
import Tr from './Tr';

export default {
  props: ['currentStatus'],
  data() {
    return {
      id: 1,
      task: '',
      tasks: [],
    };
  },
  methods: {
    addTask() {
      const addTask = this.task;
      if (
        this.tasks.every(function(val) {
          return val !== addTask;
        })
      ) {
        this.tasks.push(this.task);
      } else {
        alert('同じタスク名は登録できません');
      }

      this.task = '';
    },
    deleteTask(taskName) {
      this.tasks = this.tasks.filter(function(val) {
        return val !== taskName;
      });
    },
  },
  components: {
    Tr,
  },
};
</script>

<style scoped>
table {
  border: none;
  display: inline-block;
}
</style>
