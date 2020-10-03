<template>
  <div>
    <Title></Title>
    <StatusList @chengeStatus="currentStatus = $event"></StatusList>
    <Task :currentStatus="currentStatus"></Task>
  </div>
</template>

<script>
import Title from '../Atoms/Title';
import Task from '../Molecules/Task';
import StatusList from '../Molecules/StatusList';

export default {
  data() {
    return {
      currentStatus: '',
      task: '',
    };
  },
  components: {
    Title,
    Task,
    StatusList,
  },
};
</script>
