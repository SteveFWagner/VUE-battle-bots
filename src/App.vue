<template>
  <div id="app">
    <div id="nav">
      <button @click='toggleCreate'>Create</button>
      <h1>BATTLE BOTS!</h1>
      <button @click='toggleCollection'>Collection</button>
    </div>
    <create-bot v-if='display' :createButton='createButton'/>
    <bot-list v-else='' :bots='bots' :retireButton='retireButton'/>
  </div>
</template>

<script>
import CreateBot from './components/CreateBot'
import BotList from './components/BotList'

export default {
  name: 'app',
  data: function(){
    return{
      display:true,
      bots:[]
    }
  },
  methods:{
    toggleCreate: function(){
      this.display = true
    },
    toggleCollection: function(){
      this.display = false
    },
    createButton: function(name, attack, health){
      const newBot = {name, attack, health}
      this.bots.push(newBot)
    },
    retireButton: function(i){
      this.bots = this.bots.filter((bot, index)=> {
        return index !== i
      })
    }
  },
  components: {
    CreateBot,
    BotList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#nav{
  display: flex;
  justify-content: space-around;
}
</style>
