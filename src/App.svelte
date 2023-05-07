<script lang="ts">
  import { onMount } from 'svelte';
  import Navbar from './lib/UI/Navbar.svelte';
  import Footer from './lib/UI/Footer.svelte';
  import Timeline from './lib/UI/TImeline.svelte';

  // Employee data that would come from DB
  const employees = [
    {
      id: 'e1',
      firstName: 'denzel',
      lastName: 'braithwaite',
      title: `denzel braithwaite`, // Title is what fullcalendar displays as resource name
      email: 'denzel.braithwaite@lbpearson.com',
      username: 'd.braithwaite',
      role: 'devloper'
    },    {
        id: 'e2',
        firstName: 'jeffrey',
        lastName: 'hammond',
        title: `jeffrey hammond`,
        email: 'jeffrey.hammond@lbpearson.com',
        username: 'j.hammond',
        role: 'technician'
    },
    {
        id: 'e3',
        firstName: 'steven',
        lastName: 'lacroix',
        title: `steven lacroix`,
        email: 'steven.lacroix@lbpearson.com',
        username: 's.lacroix',
        role: 'devloper'
    },
    {
        id: 'e4',
        firstName: 'mario',
        lastName: 'mario', // His last name is actually Mario
        title: `mario mario`,
        email: 'mario.mario@lbpearson.com',
        username: 'm.mario',
        role: 'plumber'
    },
    {
        id: 'e5',
        firstName: 'lester',
        lastName: 'pearson',
        title: `lester pearson`,
        email: 'lester.pearson@lbpearson.com',
        username: 'l.pearson',
        role: 'prime minister'
    },
    {
      id: 'nt',
      title: 'nest test',
      firstName: 'nest',
      lastName: 'test',
      children: [
          {id: 'tc', title: 'test child'}
      ]
    }
  ]

  // Projects that would be created by users
  let projects = [
    {
      id: 'p1',
      resourceId: 'e1',
      title: 'Project Title',
      start: '2023-05-07',
      end: '2023-05-21'
    },
    {
      id: 'p2',
      resourceId: 'e2',
      title: 'Fix the thing',
      startRecur: '2023-05-05',
      endRecur: '2023-09-15',
      daysOfWeek: [0, 3, 6]
    },
    {
      id: 'p3',
      resourceIds: ['e3', 'e4'],
      title: 'Click me group project',
      start: '2023-05-07',
      end: '2023-05-10',
      url: 'https://www.google.ca'
    }
  ];

  // Toggle goals
  let goalsVisible = false;
  function goalsHandler() {
    goalsVisible = !goalsVisible;
  };

  // Fake Ids for now, will increment below when used
  let fakeId = 3;

  // Handle form(add project) submits
  function addProjectHandler(event) {
    fakeId ++; // Fake ID to simulate db id

    projects = [
      {
      id: "p" + fakeId.toString(),
      resourceId: event.detail.resourceId, 
      title: event.detail.title,
      start: event.detail.start,
      end: event.detail.end
      },
    ...projects]
  };
</script>

<Navbar />
<main class="mx-auto">
  <!-- TODO: Complete goals-->
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
  <Timeline {employees} {projects} on:addProject={addProjectHandler}/>
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
    background-color: #21667C;
    color: #fff;
    padding: 0.75rem 1.5rem;
    border-radius: 0.3rem;
    display: block;
    margin: 1rem 0 5rem;
  }

  button:hover,
  button:active {
    background-color: #14485a;
  }
</style>

