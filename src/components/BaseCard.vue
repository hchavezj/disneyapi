<script setup>
    const props = defineProps({
        character: {
            type: Object,
            default: () => ({
                _id: -1,
                name: 'Unknown',
                imageUrl: 'https://via.placeholder.com/150',
            }),
        },
    })
</script>

<template>
    <div :to="`/character/${props.character._id}`"
    class="rounded-lg bg-slate-900 shadow-lg">
        <img class="h-3/4 w-full rounded-t-lg object-cover object-left-top" :src="props.character.imageUrl" alt=""/>
        <h2>{{ props.character.name }}</h2>
    </div>
</template>