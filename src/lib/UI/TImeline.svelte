<script lang="ts">
    // Components
    import AddProjectForm from './AddProjectForm.svelte';

    // Svelte hooks
    import { onMount } from 'svelte';

    // FullCalendar plugins & hooks
    import { Calendar } from '@fullcalendar/core';
    import dayGridPlugin from '@fullcalendar/daygrid';
    import timeGridPlugin from '@fullcalendar/timegrid';
    import listPlugin from '@fullcalendar/list';

    // Premium FullCalendar features
    import resourceTimelinePlugin from '@fullcalendar/resource-timeline';

    // Props
    let formVisible = false;
    export let employees = [];
    export let projects = [];

    let timeline;
    onMount(() => {
        const timelineEl: HTMLElement = document.getElementById('timeline')!;

        timeline = new Calendar(timelineEl, {
            // schedulerLicenseKey: '0478426686-fcs-1616090302',
            schedulerLicenseKey: 'CC-Attribution-NonCommercial-NoDerivatives', // Trial version
            // aspectRatio: 1.5,
            height: 650,
            plugins: [ resourceTimelinePlugin ],
            initialView: 'resourceTimelineMonth',
            resources: employees,
            headerToolbar: {
                left: 'prev,today,next',
                center: 'title',
                right: 'resourceTimelineMonth,resourceTimelineYear'
            },
            events: projects,
        });
        timeline.render();
    });

  // Expand form to add project
  function formVisibilityHandler() {
    formVisible = true;
  };
</script>

<main>
  <button on:click={formVisibilityHandler}>Add Project</button>
    <div id="timeline"></div>
    {#if formVisible}
    <AddProjectForm
      actionUrl="/"
      {employees}
      {formVisible}
      on:click={() => formVisible = false}
      on:addProject/>
    {/if}
</main>

<style>
    main {
        min-height: 50vh;
    }

    
  button {
    background-color: #203952;
    color: #fff;
    padding: 0.75rem 1.5rem;
    border-radius: 0.3rem;
    display: block;
    margin: 2rem 0;
  }

  button:hover,
  button:active {
    background-color: #182b3f;
  }
</style>