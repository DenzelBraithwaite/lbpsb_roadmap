<script lang="ts">
  import { onMount } from 'svelte';
  import Navbar from './lib/UI/Navbar.svelte';
  import Footer from './lib/UI/Footer.svelte';
  import Form from './lib/UI/Form.svelte';
  import Timeline from './lib/UI/TImeline.svelte';

  // Employee data that would come from DB
  const employees = [
    {id: '01', title: 'Denzel'},
    {id: '02', title: 'Steven'},
    {id: '03', title: 'Boby'},
    {id: '04', title: 'Francois'},
    {
        id: 'nt',
        title: 'nest test',
        children: [
            {id: 'tc', title: 'test child'}
        ]
    }
  ]
</script>

<Navbar />
<main class="mx-auto">
  <!-- TODO: -->
  <h1>Goals:</h1>
  <ul class="mb-10">
    <li>Scroll endlessly through all months view. ✅</li>
    <li>Add an array of employees to populate the resources section✅</li>
    <li>Populate the resources area✅</li>
    <li>Create events, hardcoded.</li>
    <li>Create an event(project) via form, add under an employee's projects.</li>
    <li>Click on timeline event(project) to see more details.</li>
    <li>Design the TImeline better</li>
  </ul>
  <Timeline {employees}/>
</main>
<Footer />

<style>
  main {
    position: relative;
    width: 90%;
    max-width: 1200px;
    padding: 100px 0;
  }

  ul {
    list-style: square;
  }
</style>

