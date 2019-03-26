<template>
    <div>
        <p>Bot #1: {{selectionOne.name}}</p>
        <br>
        <p>Bot #2: {{selectionTwo.name}}</p>
        <button @click='battle'>Battle!</button>
        <button @click='clearInput'>Clear</button>
        <hr>
        <br>
        <bot v-for='(botObj, i) in bots' :key='i' :botObj='botObj' :retireButton='retireButton' :index='i' :selected='selected'/>
    </div>
</template>

<script>
import Bot from './Bot'
export default {
    props:['bots', 'retireButton'],
    data: function(){
        return{
            selectionOne:'',
            selectionTwo:''
        }
    },
    methods:{
        selected: function(i){
            if(!this.selectionOne){
                this.selectionOne = this.bots[i]
            }else if(this.selectionOne && !this.selectionTwo){
                this.selectionTwo = this.bots[i]
            }else{
                null
            }
        },
        battle: function(){
            if(parseInt(this.selectionOne.attack)>parseInt(this.selectionTwo.health)){
                alert('The Winner is: ' + this.selectionOne.name)
            }else if(parseInt(this.selectionTwo.attack) >= parseInt(this.selectionOne.health)){
                alert('The Winner is: ' + this.selectionTwo.name)
            }else if(parseInt(this.selectionOne.attack)*2 >= parseInt(this.selectionTwo.health)){
                alert('The Winner is: ' + this.selectionOne.name)
            }else{
                alert('The Winner is: ' + this.selectionTwo.name)
            }
            this.clearInput()
        },
        clearInput: function(){
            this.selectionOne=''
            this.selectionTwo=''
        }
    },
    components:{
        Bot
    }
}
</script>
