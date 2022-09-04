<template>
    <div :class="indicatorStyle">
        <p>{{title}}</p>
        <h2>{{indicator}}</h2>
    </div>
</template>
<script>

export default {
    name: 'Indicator',
    props: ['title','indicator','bg','color'],
    computed:{
        indicatorStyle(){
            return `h-100 p-5 rounded-3 border ${this.bg} ${this.color}`
        }
    }
}
</script>
