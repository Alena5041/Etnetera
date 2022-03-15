<template>
    <li>
        <div class="item-text">
            <span>{{index + 1 + ". "}}</span>
            <span v-if="!item.editing" @dblclick="$emit('start-edit-task', item)">{{item.title}}</span>
            <input class="input__small" v-else type="text" v-model="editedTitle" @blur="$emit('finish-edit-task', item, editedTitle)" @keyup.enter="$emit('finish-edit-task', item, editedTitle)">
        </div>
        <button @click="$emit('remove-task', item.id)" class="button__green button__small"><span class="icon check-icon"/></button>
    </li>
</template>

<script>
export default {
    name: "TaskItem",
    data () {
        return {
            editedTitle: this.item.title
        }
    },
    props: {
        item: {
            type: Object,
            required: true,
        },
        index: Number
    }
}
</script>
