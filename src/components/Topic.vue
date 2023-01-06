<template>
    <div class="topic">
        <h3>topic: {{ topic.name }}
            <i 
                    class="fas fa-times"
                    @click="onDelete(topic.guid)"
            >   
            </i> 
        </h3>
        <div 
            v-for="comment in topic.comments"
            :key="comment.date" 
        >
            <p>comment: {{ comment.comment }} </p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MyTopic',
    props: {
        topic: Object,
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