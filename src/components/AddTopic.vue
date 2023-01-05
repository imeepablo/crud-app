<template>
    <form 
        class="add-form"
        @submit="onSubmit"
    >
        <div class="form-control">
            <label>Topic</label>
            <input 
                type="text" 
                v-model="name"
                name="name"
                placeholder="Add Topic"
            />
        </div>
        <div class="form-control">
            <label>Comment</label>
            <input 
                type="comments" 
                v-model="comments"
                name="day"
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
            name: '',
            comments: '',
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()

            if(!this.name) {
                alert('Please add a topic')
                return
            }
            else if(!this.comments) {
                alert('Please add a comment')
                return
            }

            const newTopic = {
                // id: Math.floor(Math.random() * 100000),
                name: this.name,
                comments: this.comments,
            }

            this.$emit('add-topic', newTopic)
            this.name=''
            this.comments=''
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
