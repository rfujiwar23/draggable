<template>
  <div class="hello">
    <h1>Line-Up</h1>
    <draggable v-model="myArray" ghost-class="ghost" @end="onEnd">
      <transition-group type="transition" name="flip-list">
        <div class="sortable" :id="player.id" v-for="player in myArray" :key="player.id">
          <strong>{{player.name}}</strong>
          <span>{{player.id}}</span>
        </div>
      </transition-group>
    </draggable>

    <p><strong>Previous Index:</strong>{{ oldIndex }}</p>
    <p><strong>New Index:</strong>{{ newIndex }}</p>
  </div>
</template>

<script>
import draggable from 'vuedraggable'

export default {
  name: 'HelloWorld',
  components: {
    draggable
  },
  props: {
    msg: String
  },
  data(){
    return {
      myArray: [
        { name: "Giannis Antetokoumpo", id:0 },
        { name: "Khris Middleton", id:1 },
        { name: "Jrue Holiday", id:2 },
        { name: "Bobby Portis", id:3 },
        { name: "Brook Lopez", id:4 },
        { name: "Pat Connaughton", id:5 }
      ],
      oldIndex: '',
      newIndex: ''
    }
  },
  methods: {
    onEnd: function(evt) {
      console.log(evt)
      this.oldIndex = evt.oldIndex;
      this.newIndex = evt.newIndex;
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
