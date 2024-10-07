<script setup>
import MainCardSingle from './MainCardSingle.vue';


import { faker } from '@faker-js/faker';

const cards = Array.from({ length: 20 }, (_, i) => ({
  id: i + 1,
  fullname: faker.person.fullName(),
  job_title: faker.person.jobTitle(),
  bio: faker.lorem.lines(2),
  image: faker.image.urlLoremFlickr({ category: 'people' }),
  username: faker.internet.userName().toLowerCase(),
}));
</script>

<template>
  <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-10 p-10">
    <MainCardSingle 
      v-for="card in cards" 
      :key="card.id" 
      :fullname="card.fullname" 
      :job-title="card.job_title" 
      :bio="card.bio" 
      :image="card.image" 
      :username="card.username" 
    />
  </div>
</template>

<style scoped>
.grid {
  max-width: 1200px; 
  margin: 0 auto; 
}
</style>
