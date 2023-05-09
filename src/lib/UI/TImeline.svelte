<script lang="ts">
    // Svelte hooks
    import { onMount, createEventDispatcher } from 'svelte';

    // Components
    import AddProjectForm from './AddProjectForm.svelte';

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
    let employee;    

    // For creating custom events
    const createEvent = createEventDispatcher();

    // Initializing timeline
    let timeline;
    onMount(() => {
        const timelineEl: HTMLElement = document.getElementById('timeline')!;

        timeline = new Calendar(timelineEl, {
            // schedulerLicenseKey: '0478426686-fcs-1616090302',
            schedulerLicenseKey: 'CC-Attribution-NonCommercial-NoDerivatives', // Trial version
            // aspectRatio: 1.5,
            height: 600,
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

    // Simulate db id
    let fakeId = 4;
    function eventHandler(event) {
        const details = event.detail;
        
        console.log(timeline);
        // Add event(project) to timeline
        timeline.addEvent({
            id: details.projectId,
            resourceId: details.resourceId,
            title: details.title,
            description: details.description,
            start: details.start,
            end: details.end
        });

        // Custom event that passes form data on submit, data handled in parent component.
        createEvent('addProject', {
            projectId: details.projectId,
            resourceId: details.resourceId,
            title: details.title,
            description: details.description,
            start: details.startDate,
            end: details.endDate
        })
        fakeId ++;
    };
</script>

<header>
  <h2>Roadmap</h2>
</header>
<main>
  <button on:click={formVisibilityHandler}>New Project</button>
    <div id="timeline">
    </div>
    {#if formVisible}
    <AddProjectForm
      actionUrl="/"
      {fakeId}
      {employees}
      {formVisible}
      on:click={() => formVisible = false}
      on:addEvent={eventHandler}/>
    {/if}
</main>

<style>
  header {
    background-color: #26B0E4;
    margin-bottom: 2rem;
    padding: 2rem;
    border-radius: 0.25rem 0.25rem 0 0;
  }

  header > h2 {
    font-size: 2rem;
    color: #fff;
  }

  main {
    position: relative;
  }

  #timeline {
    width: 100%;
    padding: 0.125rem;
  }

  button {
    display: block;
    background-color: #3abb65;
    color: #fff;
    padding: 0.75rem 1.5rem;
    border-radius: 0.3rem;
    margin-left: 2rem;
    margin-bottom: 2rem;
  }

  button:hover,
  button:active {
    background-color: #34a058;
  }
</style>