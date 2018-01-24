<template>
  <div class="section">
    <div class="container">
      <div class="columns">
        <div class="column is-4 is-offset-4">
          <b-field>
            <b-input placeholder="enter anything..."
              type="text"
              icon="check"
              size="is-large">
            </b-input>
          </b-field>
          <b-field class="is-pulled-left">
            <b-checkbox size="is-large">test</b-checkbox>
          </b-field>
          <a class="delete is-pulled-right"></a>
          <div class="is-clearfix"></div>
          <hr>
          <button class="button is-danger is-outlined is-pulled-right">clear</button>
          <br>
          <br>
          <div>
            <section>
              2 items left
              <b-field class="is-pulled-right">
                <b-radio-button v-model="radioButton" native-value="all">
                  All (3)
                </b-radio-button>
                <b-radio-button v-model="radioButton" native-value="active">
                  Active (0)
                </b-radio-button>
                <b-radio-button v-model="radioButton" native-value="completed">
                  Completed (0)
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
      radioButton: ''
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
