<template>
    <div>
        <input type="text" placeholder="Bot Name*" v-model="name"><br>
        <input type="text" placeholder="Attack Value*" v-model="attack"><br>
        <input type="text" placeholder="Health Value*" v-model="health"><br>
        <button @click='build'>Build!</button>
        <button @click='clearInput'>Clear</button>
    </div>
</template>

<script>
export default {
    data: function(){
        return{
            name:'',
            attack:'',
            health:''
        }
    },
    methods: {
        build: function(){
            this.createButton(this.name, this.attack, this.health),
            this.clearInput()
        },
        clearInput: function(){
            this.name='',
            this.attack='',
            this.health=''
        }
    },
    props: ['createButton']
}
</script>