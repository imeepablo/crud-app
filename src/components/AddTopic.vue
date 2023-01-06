<template>
    <form 
        class="add-form"
        @submit="onSubmit"
    >
        <div class="form-control">
            <label>Topic</label>
            <input 
                v-model="topicName"
                placeholder="Add Topic"
            />
        </div>
        <div class="form-control">
            <label>Comment</label>
            <input 
                v-model="topicComment"
                placeholder="Add comment"
            />
        </div>
        <input 
            type="Submit"
            value="Save Topic"
            class="btn btn-block"
        />
    </form>
</template>

<script>

export default {
    name: 'AddTopic',
    data() {
        return {
            topicName: '',
            topicComment: '',
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()

            if(!this.topicName || !this.topicComment) {
                alert('Please add a topic and comment')
                return
            }

            const newTopic = {
                name: this.topicName,
                comments: [{ comment:this.topicComment }],
                date: new Date(),
                guid: Math.floor(Math.random() * 100000)
            }

            console.log(newTopic)

            this.$emit('add-topic', newTopic)
            this.topicName=''
            this.topicComment=''
        }
    }
}
</script>

<style scoped>

.add-form {
    margin-bottom: 40px;
}

.form-control {
    margin: 20px 0;
}

.form-control label {
    display: block;
}

.form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}

.form-control-check {
    display: flex;
}

.form-control-check label {
    flex: 1;
}

.form-control-check input {
    flex: 2;
    height: 20px;
}

</Style>
