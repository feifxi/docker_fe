<script setup>
import { onBeforeMount, ref } from 'vue';

const users = ref([])
const isLoading = ref(false)

  onBeforeMount(async () => {
    isLoading.value = true
    const host = 'lvm66125.sit.kmutt.ac.th'
    const res = await fetch(`http://${host}/api/users`)
    const data = await res.json()
    users.value = data
    isLoading.value = false
  })
</script>

<template>
  <div v-if="isLoading">
    Loading...
  </div>

  <section v-else>
    <h1 class="text-3xl">Users</h1>d
    <div v-for="user of users" class="border border-neutral-300 rounded-xl shadow p-3 font-bold">
      <p>{{ user.id }}</p>
      <p>{{ user.name }}</p>
      <p>{{ user.email }}</p>
    </div>
  </section>
</template>

<style scoped>
</style>
