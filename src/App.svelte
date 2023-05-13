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
      role: 'developer'
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
        role: 'developer'
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
<button class="btn-goals" type="button" on:click={goalsHandler}>View Goals</button>
<main class="mx-auto">
  <p class="fusion-path">Home / <span class="roadmap">Roadmap</span></p>
  <!-- TODO: Complete goals-->
  {#if goalsVisible}
  <p><mark>Here are some ideas for the Roadmap Project. Nothing is set in stone, and you are more than welcome to suggest things as we work on this.</mark></p>
     <br>
     <p class="goal">✅Compared to Microsoft Project, we want horizontal lines to be a person instead a project.</p>
     <p class="goal">🟠When creating new project/task, it would be great to allow it to be recurring. i.e., every year, in May, ABC thing needs to be updated in XYZ app.</p>
     <p class="goal">🟠A project/task should have an estimated length for completion and a deadline. The deadline is more of an indication in the project/task information. What we would see graphically on the roadmap is the start date + length.</p>
     <p class="goal">🟠When creating a project/task, it would be nice to select a color that goes with it. It could be a set of predefined colors.</p>
     <p class="goal">🟠When clicking on a project/task, we want a modal open with more info. Info could be owner, participants, quick description, start time, length, deadline…</p>
     <p class="goal">🟠We want to be able to easily jump to a specific date on the timeline.</p>
     <p class="goal">🟠Create a roadmap (someone could create their own personal roadmap)</p>
    <p class="goal">🛑Invite people to collaborate on a roadmap. (this can be worked on later once we integrate users)</p>
    <p class="goal">🛑You can only see a roadmap if you are invited (part of it).</p>
    <p class="goal">🛑Permissions can be given to edit / add to the roadmap.</p>
    <p class="goal">🛑Users can only edit their own project/task on the roadmap.</p>
    <p class="goal">🛑When creating a project/task, allow to add participants. These participants will now have the project/task under their name, but they would not be able to edit it. Only the owner can edit.</p>
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

  .goal {
    margin-bottom: 0.75rem;
  }

  .btn-goals {
    color: #fff;
    margin-left: 2rem;
  }

  .btn-goals:hover {
    background-color: transparent;
    padding: 0;
    text-decoration: underline;
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

