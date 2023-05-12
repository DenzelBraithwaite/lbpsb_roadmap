<script lang="ts">
  import { onMount } from 'svelte';
  // import Navbar from './lib/UI/Navbar.svelte';
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
    },
    {
        id: 'e1000',
        firstName: 'other',
        lastName: 'other0',
        title: `other other0`,
        email: 'other.other0@lbpearson.com',
        username: 'o.other0',
        role: 'other'
    },
    {
        id: 'e10001',
        firstName: 'other',
        lastName: 'other1',
        title: `other other1`,
        email: 'other.other1@lbpearson.com',
        username: 'o.other1',
        role: 'other'
    },
    {
        id: 'e10002',
        firstName: 'other',
        lastName: 'other2',
        title: `other other2`,
        email: 'other.other2@lbpearson.com',
        username: 'o.other2',
        role: 'other'
    },
    {
        id: 'e10003',
        firstName: 'other',
        lastName: 'other3',
        title: `other other3`,
        email: 'other.other3@lbpearson.com',
        username: 'o.other3',
        role: 'other'
    },
    {
        id: 'e10004',
        firstName: 'other',
        lastName: 'other4',
        title: `other other4`,
        email: 'other.other4@lbpearson.com',
        username: 'o.other4',
        role: 'other'
    },
    {
        id: 'e10005',
        firstName: 'other',
        lastName: 'other5',
        title: `other other5`,
        email: 'other.other52@lbpearson.com',
        username: 'o.other',
        role: 'other'
    },
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

  // Handle form(add project) submits
  function addProjectHandler(event) {
    const details = event.detail;

    projects = [
      {
      id: details.projectId,
      resourceId: details.resourceId, 
      title: details.title,
      start: details.start,
      end: details.end
      },
    ...projects]
  };
</script>

<!-- <Navbar /> -->
<Navbar />
<button on:click={goalsHandler}>View Goals</button>
<main class="mx-auto">
  <p class="fusion-path">Home / <span class="roadmap">Roadmap</span></p>
  <!-- TODO: Complete goals-->
  {#if goalsVisible}
  <ul id="goals" class="mb-10">
    <li>Scroll endlessly through all months view. ✅</li>
    <li>Add an array of employees to populate the resources section✅</li>
    <li>Populate the resources area✅</li>
    <li>Create events, hardcoded✅.</li>
    <li>Create an event(project) via form, add under an employee's projects.✅</li>
    <li>Redesign simple 'modal/card' for event detail hover, because you're smart and deleted it</li>
    <li>Click on timeline event(project) to see more details.</li>
    <li>Fix layout, match MS project</li>
    <li>Design the TImeline better</li>
  </ul>
  {/if}
  <Timeline {employees} {projects} on:addProject={addProjectHandler}/>
</main>
<!-- <Footer /> -->

<style>
  :global(body) {
    background: url('/img/fusion-bg.png');
    background-repeat: no-repeat;
    background-size: cover;
    min-height: 100vh;
    padding-bottom: 10rem;
  }

  main {
    position: relative;
    width: 80%;
    max-width: 1200px;
    background-color: #fff;
    border-radius: 0.25rem;
  }

  ul {
    list-style: square;
    list-style-position: inside;
  }

  
  button {
    text-decoration: underline;
    color: #fff;
    margin-left: 2rem;
  }

  button:hover,
  button:active {
    background-color: #3abb65;
    text-decoration: none;
    padding: 0.75rem 1.5rem;
    border-radius: 0.3rem;
  }

  .fusion-path {
    color: #fff;
    position: absolute;
    top: -2rem;
  }

  .roadmap {
    color: #26B0E4;
  }
</style>

