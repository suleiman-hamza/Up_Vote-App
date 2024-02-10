<template>
    <article class="media">
      <div class="media_icon"></div>
      <div class="media_desc">
        <h3>{{ user.club }}</h3>
        <p>Coach: {{ user.coach }}</p>
        <p>{{ user.motto }}</p>
      </div>
      <div class="media_votes">
        <p>{{ user.votes }}</p>
        <button type="button" v-on:click="increase(user.id)">+</button>
      </div>
    </article>
</template>

<script setup>
    const props = defineProps(['sortedUsers', 'increase', 'user', 'submission'])
</script>