<template>
  <RouterLink :to="{ name: 'CardDetails', params: { id: username }}">
    <div class="card">
      <img :src="image" class="card-image" alt="Card image" />
      <div class="card-content">
        <p class="card-title">{{ fullname }}</p>
        <p class="card-job">{{ job_title }}</p>
        <p class="card-bio">{{ bio }}</p>
      </div>
    </div>
  </RouterLink>
</template>

<script setup>
defineProps(['fullname', 'jobTitle', 'bio', 'image', 'username']);
</script>

<style scoped>
.card {
  background-color: #4caf50; 
  border-radius: 12px; 
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); 
  transition: transform 0.3s, box-shadow 0.3s; 
  overflow: hidden; 
  cursor: pointer; 
  height: 400px; 
  color: white; 
}

.card:hover {
  transform: translateY(-5px); 
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2); 
}

.card-image {
  width: 100%; 
  height: 200px; 
  object-fit: cover; 
}

.card-content {
  padding: 20px; 
  height: 180px; 
}

.card-title {
  font-size: 1.2em; 
  margin-bottom: 5px; 
}

.card-job {
  font-size: 0.9em; 
  margin-bottom: 10px; 
}

.card-bio {
  font-size: 0.8em; 
  line-height: 1.5; 
}
</style>
