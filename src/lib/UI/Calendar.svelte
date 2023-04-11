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
      droppable: true, // This allows things to be dropped onto the calendar
      dateClick: function(info) {
        // Do something more meaningful here
        // let dateString: String = info.dateStr;
        // alert(`You clicked on: ${dateString}`)


          if(info.dayEl.style.backgroundColor !== 'rgba(197, 241, 255, 0.525)'){
            // Open a modal with more info about event/project
            info.dayEl.style.backgroundColor = '#c5f1ff86';
            
          } else {
            info.dayEl.style.backgroundColor = 'white';
          }
    }});

    // Initiate calendar 
    calendar.render();
  });
  
  function formVisibilityHandler() {
    formVisible = false;
  }
  
  function submitHandler(event) {
    calendar.addEvent(event.detail);
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

