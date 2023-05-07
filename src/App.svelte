<script lang="ts">
  import { onMount } from 'svelte';
  import Navbar from './lib/UI/Navbar.svelte';
  import Footer from './lib/UI/Footer.svelte';
  import Form from './lib/UI/Form.svelte';
  import Timeline from './lib/UI/TImeline.svelte';

  // Employee data that would come from DB
  const employees = [
    {id: 'e01', title: 'Denzel'},
    {id: 'e02', title: 'Steven'},
    {id: 'e03', title: 'Boby'},
    {id: 'e04', title: 'Francois'},
    {
        id: 'nt',
        title: 'nest test',
        children: [
            {id: 'tc', title: 'test child'}
        ]
    }
  ]

  let projects = [
    {
      id: 'p01',
      resourceId: 'e01',
      title: 'Project Title',
      start: '2023-05-07',
      end: '2023-05-21'
    },
    {
      id: 'p02',
      resourceId: 'e02',
      title: 'Fix the thing',
      startRecur: '2023-05-05',
      endRecur: '2023-09-15',
      daysOfWeek: [0, 3, 6]
    },
    {
      id: 'p03',
      resourceIds: ['e03', 'e04'],
      title: 'Click me group project',
      start: '2023-05-07',
      end: '2023-05-10',
      url: 'https://www.google.ca'
    }
  ];

  // Toggle goals
  let goalsVisible = false;
  const goalsHandler = () => {
    goalsVisible = !goalsVisible;
  };
</script>

<Navbar />
<main class="mx-auto">
  <!-- TODO: -->
  <button on:click={goalsHandler}>View Goals</button>
  {#if goalsVisible}
  <ul id="goals" class="mb-10">
    <li>Scroll endlessly through all months view. ✅</li>
    <li>Add an array of employees to populate the resources section✅</li>
    <li>Populate the resources area✅</li>
    <li>Create events, hardcoded✅.</li>
    <li>Create an event(project) via form, add under an employee's projects.</li>
    <li>Click on timeline event(project) to see more details.</li>
    <li>Fix layout, match MS project</li>
    <li>Design the TImeline better</li>
  </ul>
  {/if}
  <Timeline {employees} {projects}/>
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
    list-style-position: inside;
  }

  button {
    background-color: #203952;
    color: #fff;
    padding: 0.75rem 1.5rem;
    border-radius: 0.3rem;
    margin-bottom: 2rem;
  }

  button:hover,
  button:active {
    background-color: #182b3f;
  }
</style>

