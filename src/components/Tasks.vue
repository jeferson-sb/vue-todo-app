<template>
  <section class="content">

    <div class="holder">
      <form @submit.prevent="addTask" class="form">
        <transition name="alert-in" enter-active-class="animated fadeIn" leave-active-class="animated fadeOut">
          <p class="form__alert" v-if="errors.has('task')">{{ errors.first('task') }}</p>
        </transition>
        <input type="text" placeholder="Insira sua tarefa ... " v-model="task" v-validate="'min:5'" name="task" class="form__input-text">
      </form>

      <ul class="list-tasks">
        <transition-group name="list" enter-active-class="animated fadeIn" leave-active-class="animated fadeOut">
          <li v-for="(data, index) in tasks" :key="index" class="list-tasks__items">
              <input type="checkbox" class="toggle" v-model="data.done" :id="data.task">
              <button class="list-tasks__removebtn" v-on:click="editTask(index)">Editar</button>
              <button class="list-tasks__removebtn" v-on:click="removeTask(index, data.task)">Excluir</button>
              <button class="list-tasks__removebtn" v-on:click="saveTask(index)" v-show="data.edit">Salvar</button>
            <label :class="[{lineThrough: data.done}, {focusTask: data.edit}]" :contenteditable="data.edit" :for="data.task"> {{ data.task }}

            </label>

          </li>
        </transition-group>
      </ul>
      <p v-if="tasks.length === 0">Você não possui nenhuma tarefa pendente 😄 </p>
    </div>
  </section>
</template>

<script>
export default {
  name: "Tasks",
  data() {
    return {
      appName: "Todo App",
      task: "",
      tasks: [
        { task: "Estudar Matemática", done: false, edit: false },
        { task: "Ir ao mercado", done: false, edit: false }
      ]
    };
  },
  methods: {
    addTask() {
      this.$validator.validateAll().then(result => {
        if (result) {
          this.tasks.push({ task: this.task, edit: false });
          this.task = "";
        }
      });
    },
    removeTask(task) {
      this.tasks.splice(task, 1);
    },
    editTask(task) {
      this.tasks[task].edit = true;
    },
    saveTask(index) {
      this.tasks[index].edit = false;
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/css/animate.css";
@import "../assets/scss/styles.scss";
</style>


