<template>
  <div class="about">
    <h1>{{ msg }}</h1>
    <h1>{{ mmm }}</h1>
    <button @click="addTodo()">Press1</button>
    <button @click="removeTodo()">Press2</button>
    <h2>{{ newTodoText }}</h2>
    <AboutInput
      v-model="fuck"
      placeholder="Kick Your Ass"
      @keydown.enter="something"
    />
    <p>
      {{newTodoText2}}
    </p>
  </div>
</template>

<script>
import AboutInput from "./AboutInput.vue";
export default {
	components: {
	  AboutInput
	},
  name: "About",
  props: {
    msg: String,
    mmm: Number
  },
  data() {
    return {
      newTodoText: "Hey",
      fuck: "",
      newTodoText2: ""
    };
  },
  mounted: function () {
    this.addTodo();
  },
  methods: {
    addTodo() {
      this.newTodoText = "Fuck you";
    },
    removeTodo() {
      this.newTodoText = "Sucker";
    },
    something() {
      this.newTodoText2 = this.fuck;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
