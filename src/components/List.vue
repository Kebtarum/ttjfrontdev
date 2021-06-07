<template>
    <div :key="item.id" v-for="item in list" >
        <Item  @delete-item="$emit('delete-item', item.id)" :item="item" />
    </div>
</template>

<script>
import Item from './Item'

export default {
    name: 'List',
    props: {
        list: Array
    },
    components: {
        Item
    },
    emits: ['delete-item']
}
</script>