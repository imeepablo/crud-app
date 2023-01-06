<template>
    <div 
      v-for="topic in topics"
      :key="topic.guid" 
   >
      <Topic 
         :topic=topic
         @delete-topic="$emit('delete-topic',topic.guid)"
         />
    </div>
</template>
 
<script>
import Topic from './Topic.vue'
export default {
   name: 'MyTopics',
   components: {
      Topic,
   },
   emits: ['delete-topic'],
   props: {
    topics: Array
   }
}
</script>
