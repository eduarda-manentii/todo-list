<template>
  <div
  @click="$emit('taskStateChanged', task)"
  class="task"
  :class="stateClass">
    <span @click.stop="$emit('taskDeleted', task)" class="close"> x </span>
    <p> {{  task.name }} </p>
  </div>
</template>

<script>
export default {
  props: {
    task: { type: Object, required: true}
  },
  computed: {
    stateClass() {
      return {
        pending: this.task.pending,
        done: !this.task.pending
      }
    }
  }
}
</script>

<style>

 .task {
  position: relative;
    box-sizing: border-box;
    width: 350px;
    height: 150px;
    padding: 10px;
    border-radius: 8px;
    font-size: 2rem;
    font-weight: 300;
    cursor: pointer;
    user-select: none;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .pending {
    border-left: 12px solid red;
    background-color:  rgb(207, 46, 46);
  }

  .done {
    color: white;
    border-left: 12px solid green;
    background-color: rgb(74, 187, 74);
    text-decoration: line-through;
  }

  .pending .close {
    background-color: red;
  }

  .done .close {
    background-color:  green;
  }

  .close {
    position: absolute;
    right: 10px;
    top: 10px;
    font-size: 0.9rem;
    font-weight: 600;
    height: 20px;
    width: 20px;
    border-radius: 10px;
    display: flex;
    justify-content: center;
  }
</style>
