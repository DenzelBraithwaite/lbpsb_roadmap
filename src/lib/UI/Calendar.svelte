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
      initialView: 'multiMonthYear',
      multiMonthMaxColumns: 1,
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
      events: [
        {
          title: 'Boilerplate Title',
          description: 'Boilerplate description',
          start: '2023-04-20',
          end: '2023-04-28'
        }
      ],
      eventClick: function(info) {
        // Create modal
        const eventModal = document.createElement('div');
        eventModal.classList.add('event-modal');

        // Add modal content
        const eventModalContent = document.createElement('div');
        eventModalContent.classList.add('event-modal-content');
        eventModalContent.innerHTML = "<h1>Test, hello from Modal world</h1>"
        
        // Add modal content to Modal
        eventModal.appendChild(eventModalContent);

        // Add modal to DOM
        document.body.appendChild(eventModal);

        // modalContent.innerHTML = '<h2>' + info.event.title + '</h2><p>' + info.event.extendedProps.description + '</p>';
        
        // close modal window when clicked outside
        // window.addEventListener('click', function(event) {
        //   if (event.target == modal) {
        //     modal.remove();
        //   }
        // })
      },
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
<div id="calendar" class="rounded p-8 shadow-lg"></div>
<div class="event-modal2">Hey</div>

{#if formVisible}
  <Form on:formSubmit={submitHandler} filePath='#' on:click={formVisibilityHandler}/>
{/if}

<style>
  #calendar {
    box-shadow: 0 2px 8px #00000025;
    height: 750px;
  }

  .event-modal {
    height: 100px;
    width: 100px;
    background-color: red;
    border-radius: 4px;

    position: absolute;
    top: 100px;
    left: 100px;
  }

  .event-modal-content {
    padding: 1rem;
    background-color: greenyellow;
  }

  .event-modal2 {
    height: 100px;
    width: 100px;
    background-color: blue;
    border-radius: 4px;

    position: absolute;
    top: 100px;
    right: 100px;
  }
</style>

