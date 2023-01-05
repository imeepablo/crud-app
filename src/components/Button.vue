<template>
    <button 
        class="btn"
        :style="{background:color}"
        >
        <!-- @click="onClick" -->
        Create
        {{text}}
    </button>
</template>

<script>
export default {
    name: 'VButton',
    props: {
        text: String,
        color: String,
    },
    // methods: {
    //     onClick() {
    //      this.$emit('btn-click')
    //     }
    // }
}
</script>