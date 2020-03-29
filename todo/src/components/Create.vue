<template>
  <div>
    <form class="create-form">
      <div class="create">
        <input type="text" placeholder="Create Todo" class="create-input" v-model="currentTodo" />
        <input type="submit" value="Submit" class="create-btn" @click="addTodo" />
      </div>

      <div class="display-todo">
        <!-- This div is being seperated per each item in todo list -->
        <div v-bind:key="index" v-for="(data, index) in todo" @click="markComplete(index)">
          <div class="looped-div">
            <h1 class="title">{{ data.title }}</h1>
          </div>
          <br />
        </div>
      </div>
    </form>
  </div>
</template>

<script>
import date from "date-and-time";

export default {
  name: "Create",
  data() {
    return {
      currentTodo: "",
      todo: [
        {
          title: "hey",
          completed: false
        },
        {
          title: "heys",
          completed: false
        }
      ]
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      if (this.currentTodo == "") {
        alert("Enter a todo");
      } else {
        this.todo.push({
          id: 2,
          title: this.currentTodo,
          time: date.format(new Date(), `hh:mm A`)
        });
        this.currentTodo = "";
      }
    },
    markComplete(id) {
      this.todo.splice(id, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,500i,600&display=swap");

.create {
  width: 80%;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto;
}
.create-input,
.create-btn {
  width: 30%;
  margin: 20px 5px 0px 0px;
  height: 50px;
}
.create-input {
  position: relative;
  left: 200px;
  justify-self: right;
  width: 110%;
  border-radius: 5px;
  border: 1px solid lightgrey;
  font-size: 20px;
}
.create-btn {
  position: relative;
  left: 200px;
  background-color: #1e90ff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  box-shadow: 0px 1px 3px 0px;
}
.display-todo {
  background-color: #fff;
  width: 80%;
  margin: 0 auto;
  margin-top: 8vh;
  height: 70vh;
  overflow: scroll;
}
.looped-div {
  transition: ease-in 500ms;
  position: relative;
  background: #182c61;
  width: 50%;
  margin: 0 auto;
  height: 8vh;
  display: grid;
  justify-content: center;
  align-content: center;
  font-family: "Montserrat", sans-serif;
  font-size: 0.9rem;
  color: #fff;
  border-left: solid 3px #0652dd;
  cursor: pointer;
  top: 5px;
}
.line {
  text-decoration: line-through;
}
.looped-div:hover {
  transition: ease-out 500ms;
  width: 75%;
  border-top: solid 3px #0652dd;
  filter: saturate(20%);
  text-decoration: line-through;
}
</style>
