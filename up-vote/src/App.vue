<template>
  <main>
    <h1 class="title">Premire League</h1>
    <!--single submission component with props passed to child component-->
    <Submission 
      v-for="(user, index) in sortedUsers" 
      :sortedUsers="sortedUsers" 
      :user="user" 
      :increase="increase"
      :submission="submission"
      :key="index"
      :class="{active: sortedUsers.votes >= 60}"
    />
  </main>
</template>

<script setup>
import { ref, computed } from 'vue';
import Submission from './components/Submission.vue';

//initial user data before being sorted
let users = ref([
  {
    id: 1,
    club: 'Arsenal',
    coach: 'Mikel Arterta',
    motto: 'Gunners',
    votes: 52
  },
  {
    id: 2,
    club: 'Manchester city',
    coach: 'Pep Guardiola',
    motto: 'Sky Blue',
    votes: 45
  },
  {
    id: 3,
    club: 'Manchetser United',
    coach: 'Ten Hag',
    motto: 'Red Devils',
    votes: 48
  },
  {
    id: 4,
    club: 'Liverpool',
    coach: 'Jurgen klopp',
    motto: 'YMWA',
    votes: 43
  },
  {
    id: 5,
    club: 'Chelsea',
    coach: 'Ancelotti',
    motto: 'The Blues',
    votes: 5
  }
])

//sorted user data by votes
const sortedUsers = computed(() => {
  return users.value.sort((a, b) => {
    return b.votes - a.votes 
  })
})

//increment button logic, find userid and increase the votes
const increase = (userid) => {
  console.log(userid)
  const submission = users.value.find((sumb) => {
      return sumb.id === userid
    });
  submission.votes++
}
</script>

<style>
h3, p {
  margin-top: 0;
}
.title {
  text-align: center;
}
.media {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  border: 2px solid grey;
  padding: 1rem;
}
.media_icon {
  display: inline-block;
  width: 105px;
  height: 105px;
  background-color: chocolate;
}
.media_votes {
  margin-left: auto;
}
.active {
  color: red;
}
</style>
