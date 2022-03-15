<template>
    <div>
        <form @submit.prevent="onSubmit">
            <input class="input__big" type="text" v-model="title" placeholder="Add new task"/>
            <button class="button__blue button__big" type="submit"><span class="icon add-icon"/></button>
        </form>
    </div>
</template>

<script>
export default {
    name: "AddTask",
    data () {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit () {
            if (this.title.trim()) {
                const newItem = {
                    id: Date.now(),
                    title: this.title,
                }
                this.$emit('add-task', newItem)
                this.title = ''
            }
        },
    }
}
</script>
