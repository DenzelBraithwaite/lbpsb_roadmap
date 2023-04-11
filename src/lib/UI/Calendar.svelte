<script lang="ts">
  // From Svelte
  import { onMount } from 'svelte';

  // Full Calendar Plugins
  import { Calendar } from '@fullcalendar/core';
  import dayGridPlugin from '@fullcalendar/daygrid';
  import timeGridPlugin from '@fullcalendar/timegrid';
  import listPlugin from '@fullcalendar/list';

  // Unused right now
  import interactionPlugin from '@fullcalendar/interaction';
  import multiMonthPlugin from '@fullcalendar/multimonth';
  // import scrollGridPlugin from '@fullcalendar/scrollgrid'; // Req. premium

  // Import custom components
  import Form from './Form.svelte';
  
  $: formVisible = false;
  let calendar;

  onMount(() => {
    const calendarEl: HTMLElement = document.getElementById('calendar')!;
    calendar = new Calendar(calendarEl, {
      // schedulerLicenseKey: '<YOUR-LICENSE-KEY-GOES-HERE>',
      plugins: [ 
        dayGridPlugin,
        timeGridPlugin,
        listPlugin,
        interactionPlugin,
        multiMonthPlugin
      ],
      initialView: 'dayGridMonth',
      selectable: true,
      droppable: true, // This allows things to be dropped onto the calendar
      dragScroll: true, // Let's user drag off the calendar and have it keep scrolling.
      headerToolbar: {
        right: 'prev,next',
        center: 'title',
        left: 'dayGridMonth,timeGridWeek,timeGridDay,today'
      },
      footerToolbar: {
        right: '',
        center: 'addEventButton',
        left: ''
      },
      customButtons: {
        addEventButton: {
          text: 'New Project',
          click: function() {
            formVisible = true;
          }
        }
      },
      events: [],
      dateClick: function(info) {
        // Open a modal with more info about event/project
            
    }});

    // Initiate calendar 
    calendar.render();
  });
  
  function formVisibilityHandler() {
    formVisible = false;
  }
  
  function submitHandler(event) {
    calendar.addEvent(event.detail);
    formVisible = false;
  };

</script>
<div id="calendar"></div>

{#if formVisible}
  <Form on:formSubmit={submitHandler} filePath='#' on:click={formVisibilityHandler}/>
{/if}

<style>
  #calendar {
    padding: 2rem;
    height: 800px;
  }
</style>

