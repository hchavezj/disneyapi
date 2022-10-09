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
  <RouterLink
    :to="`/character/${props.character._id}`"
    class="rounded-lg bg-slate-900 shadow-lg"
  >
    <img
      class="h-3/4 w-full rounded-t-lg object-cover object-top"
      :src="props.character.imageUrl"
    />
    <h2 class="text-center text-2xl font-semibold text-gray-400">
      {{ props.character.name }}
    </h2>
  </RouterLink>
</template>
