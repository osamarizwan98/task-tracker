<template>
    <button @click="onClick()" class="btn" :style="{background: color}" type="button">{{text}}</button>
</template>
<script>
export default {
    name: 'Button',
    props: {
        text : String,
        color: String
    },
    methods: {
        onClick(){
            this.$emit('toggle-add-task')
        }
    }
}
</script>
