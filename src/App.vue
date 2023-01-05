<template>
  <div class="container">
    <h1>Vue 3 Topic App:</h1>
    <!-- <Button>Create</Button> -->
    <AddTopic @add-topic="addTopic"/>
    <Topics @delete-topic="deleteTopic" :topics="topics"/>
  </div>
</template>

<script>
// import Button from './components/Button.vue'
import Topics from './components/Topics.vue'
import AddTopic from './components/AddTopic.vue'

export default {
  name: 'App',
  components: {
    // Button,
    Topics,
    AddTopic,
  },
  data() {
    return {
      topics: [],
    }
  },
  methods: {
    addTopic(topic){
      this.topics = [...this.topics, topic]
    },


    // async addTopic(topic) {
    //   const res = await fetch('api/topics', {
    //     method: 'POST',
    //     headers: {
    //       'Content-type': 'application/json',
    //     },
    //     body: JSON.stringify(topic),
    //   })

    //   const data = await res.json()
        
    //   this.topics = [...this.topics, data]
    // },


    deleteTopic(guid){
      this.topics = this.topics.filter((topic) => topic.guid !== guid)
    },


    // async deleteTopic(guid){
    //   if (confirm('Are you sure?')) {
    //     const res = await fetch(`api/topics/${guid}`, {
    //       method: 'DELETE'
    //     })
    //     res.status === 200 ? (this.topics = this.topics.filter((topic)=>topic.guid !== guid)) 
    //     : alert('Error deleting topics')
    //   }
    // },

    async fetchTopics() {
      const res = await fetch('api/topics')

      const data = await res.json()
      return data
    },
    async fetchTopic(guid) {
      const res = await fetch(`api/topics/${guid}`)

      const data = await res.json()
      return data
    }
  },
  async created() {
    this.topics = await this.fetchTopics()
  }
 }
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 1300px;
  margin: 30px auto;
  overflow: auto;
  min-height: 750px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
  
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

  .btn:focus {
    outline: none;
  }

  .btn:active {
    transform: scale(0.98);
  }

  .btn-block {
    display: block;
    width: 100%;
  }

</style>
