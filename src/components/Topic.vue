<template>
    <div class="topic">
      <h3>topic: {{ topic.name }}
        <i 
                class="fas fa-times"
                @click="onDelete(topic.guid)"
        >   
        </i> 
    </h3>
      <p>comment: {{ topic.comments }}</p>
    </div>
</template>

<script>
export default {
    name: 'MyTopic',
    props: {
        topic: Object
    },
    methods: {
        onDelete(guid) {
            this.$emit('delete-topic', guid)
        }
    }

}
</script>
   
<style scope>
.fas {
    color: red;
}
.topic {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}

.topic h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;    
}
</style>