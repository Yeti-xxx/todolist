<template>
  <form class="form-inline" @submit.prevent="onFormSubmit">
    <div class="input-group mb-2 mr-sm-2">
      <div class="input-group-prepend">
        <div class="input-group-text">任务</div>
      </div>
      <input v-model.trim="task" class="form-control" id="inlineFormInputGroupUsername2" placeholder="输入..."
        style="width:692px">
    </div>
    <button type="submit" class="btn btn-primary mb-2">添加任务</button>
  </form>
</template>

<script>
export default {
  name: 'TodoInput',
  data() {
    return {
      task: ''
    }
  },
  emit: ['add'],
  methods: {
    onFormSubmit() {
      if (!this.task) {
        return alert('任务内容不能为空！');
      }
      this.$emit('add', this.task);
      this.task = '';
    }
  }
}

</script>

<style lang='less' scoped>
</style>
