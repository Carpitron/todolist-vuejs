<template>
  <li>
    <button @click.self="$emit('complete')" :class="className">
      <i class="far fa-circle"></i> {{ task.title }}
    </button> 
    <button @click="$emit('remove')"><i class="far fa-trash-alt"></i></button>
  </li>
</template>

<script>
export default {
  name: "TodoList",
  props: ["task"],
  computed: {
    className() {
      let classes = ['toggle'];
      if(this.task.completed) {
        classes.push('toggle-completed');
      }
      return classes.join(' ');
    }
  }
};
</script>

<style>
.fa-trash-alt{color: crimson;
padding-left: 500px;
}

li{display: flex;

justify-content: center;}
</style>
