<script lang="ts">
  import { onMount } from 'svelte';
  import Navbar from './lib/UI/Navbar.svelte';
  import Footer from './lib/UI/Footer.svelte';
  import Calendar from './lib/UI/Calendar.svelte';
  import Form from './lib/UI/Form.svelte';

  let userEvents = [];

  function newProjectHandler(event) {
    userEvents.push(event.detail);
    console.log(userEvents);
  };
</script>

<Navbar />
<main>
  <!-- <Form filePath='./lib/UI/Calendar' on:addProject={newProjectHandler}/> -->
  <Calendar />
</main>
<Footer />

<style>
  main {
    padding: 150px 0;
  }
</style>

