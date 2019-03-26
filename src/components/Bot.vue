<template>
    <div>
        <h5>{{botObj.name}}</h5>
        <p>Attack:{{botObj.attack}}</p>
        <p>Health:{{botObj.health}}</p>
        <button @click='selected(index)'>Select</button>
        <button @click='retireButton(index)'>Retire</button>
    </div>
</template>

<script>
export default {
    props:['botObj', 'index', 'retireButton', 'selected']
}
</script>