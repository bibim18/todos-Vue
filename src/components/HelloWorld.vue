<template>
  <div class="section">
    <div class="container">
      <div class="columns">
        <div class="column is-4 is-offset-4">
          <b-field>
            <b-input placeholder="enter anything..."
              type="text"
              icon="check"
              size="is-large"
              @keyup.native.enter="addTodos"
              v-model="todo">
            </b-input>
          </b-field>
          <div v-for="(a, index) in todos" :key="a.title" v-if="radioButton === all">
            <b-field class="is-pulled-left">
              <b-checkbox v-if="a.completed === true" size="is-large" @input="changeToComplete(index, $event)"><strike>{{a.title}}</strike></b-checkbox>
              <b-checkbox v-if="a.completed === false" size="is-large" @input="changeToComplete(index, $event)">{{a.title}}</b-checkbox>
            </b-field>
            <a class="delete is-pulled-right is-large" @click="deleteTodos(index)"></a>
            <div class="is-clearfix"></div>
          </div>
          <div v-for="(a, index) in todos" :key="a.title" v-if="radioButton === active">
            <b-field class="is-pulled-left">
              <b-checkbox v-if="a.completed === true" size="is-large" @input="changeToComplete(index, $event)"><strike>{{a.title}}</strike></b-checkbox>
              <b-checkbox v-if="a.completed === false" size="is-large" @input="changeToComplete(index, $event)">{{a.title}}</b-checkbox>
            </b-field>
            <a class="delete is-pulled-right is-large" @click="deleteTodos(index)"></a>
            <div class="is-clearfix"></div>
          </div>
          <div v-for="(a, index) in todos" :key="a.title" v-if="radioButton === completed">
            <b-field class="is-pulled-left">
              <b-checkbox v-if="a.completed === true" size="is-large" @input="changeToComplete(index, $event)"><strike>{{a.title}}</strike></b-checkbox>
              <b-checkbox v-if="a.completed === false" size="is-large" @input="changeToComplete(index, $event)">{{a.title}}</b-checkbox>
            </b-field>
            <a class="delete is-pulled-right is-large" @click="deleteTodos(index)"></a>
            <div class="is-clearfix"></div>
          </div>
          <hr>
          <button class="button is-danger is-outlined is-pulled-right" @click="clearCompleted">clear</button>
          <br>
          <br>
          <div>
            {{radioButton}}
            <section>
              {{todos.length}} items left
              <b-field class="is-pulled-right">
                <b-radio-button v-model="radioButton" native-value="all" @click="changeShowDisplay()">
                  All ({{all}})
                </b-radio-button>
                <b-radio-button v-model="radioButton" native-value="active" @click="changeShowDisplay()">
                  Active ({{active}})
                </b-radio-button>
                <b-radio-button v-model="radioButton" native-value="completed" @click="changeShowDisplay()">
                  Completed ({{completedTodos}})
                </b-radio-button>
              </b-field>
            </section>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      radioButton: 'all',
      todo: '',
      todos: []
    }
  },
  methods: {
    addTodos () {
      this.todos.push({
        title: this.todo,
        completed: false
      })
      this.todo = ''
    },
    deleteTodos (index) {
      this.todos.splice(index, 1)
    },
    changeToComplete (index, event) {
      this.todos[index].completed = event
    },
    clearCompleted () {
      for (var i = this.todos.length - 1; i >= 0; i--) {
        if (this.todos[i].completed === true) {
          this.todos.splice(i, 1)
        }
      }
    }
  },
  computed: {
    all () {
      return this.todos.length
    },
    active () {
      var count = 0
      for (var i = this.todos.length - 1; i >= 0; i--) {
        if (this.todos[i].completed === false) {
          count++
        }
      }
      return count
    },
    completedTodos () {
      return this.todos.filter(todo => todo.completed === true).length
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
