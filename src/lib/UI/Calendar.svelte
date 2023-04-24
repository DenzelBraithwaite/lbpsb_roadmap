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
      droppable: false, // This allows things to be dropped onto the calendar
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
        eventModal.innerHTML = `
          <div class="event-modal z-20 absolute top-1/2 left-1/2 bg-white rounded p-5 shadow-lg">
            <p class="text-sm font-bold">Title</p>
            <p class="text-xl mb-5 border-b border-grey">Some project title</p>
            <p class="text-sm font-bold">Start</p>
            <p class="text-sm mb-5">04/04/2023</p>
            <p class="text-sm font-bold">End</p>
            <p class="text-sm mb-5">04/09/2023</p>
            <p class="text-sm font-bold">Status</p>
            <select name="status" id="status" class="border w-full mb-5 p-1">
              <option value="not set">Not set</option>
              <option value="on track">On track</option>
              <option value="at risk">At risk</option>
              <option value="high risk">High risk</option>
              <option value="done">Done</option>
            </select>
            <button class="border px-3 py-2">Open details</button>
          </div>
        `;
        eventModal.classList.add(
          // Using tailwind above in innerHTML instead
        );

        // Add modal content
        const eventModalContent = document.createElement('div');
        eventModalContent.classList.add('event-modal-content');
        eventModalContent.innerHTML = "<h1>Test, hello from Modal world, inner content</h1>"
        
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

{#if formVisible}
  <Form on:formSubmit={submitHandler} filePath='#' on:click={formVisibilityHandler}/>
{/if}
<!-- <div class="event-modal z-20 absolute top-1/2 left-1/2 bg-white rounded p-5 shadow-lg">
  <p class="text-sm font-bold">Title</p>
  <p class="text-xl mb-5 border-b border-grey">Some project title</p>
  <p class="text-sm font-bold">Start</p>
  <p class="text-sm mb-5">04/04/2023</p>
  <p class="text-sm font-bold">End</p>
  <p class="text-sm mb-5">04/09/2023</p>
  <p class="text-sm font-bold">Status</p>
  <select name="status" id="status" class="border w-full mb-5 p-1">
    <option value="not set">Not set</option>
    <option value="on track">On track</option>
    <option value="at risk">At risk</option>
    <option value="high risk">High risk</option>
    <option value="done">Done</option>
  </select>
  <button class="border px-3 py-2">Open details</button>
</div> -->
<style>
  #calendar {
    box-shadow: 0 2px 8px #00000025;
    height: 750px;
  }

  .event-modal {
    /* Empty because styles weren't applying after elem was created.
    Used tailwind instead, that seemed to work. */
  }

  /* Not used currently */
  .event-modal-content {
    padding: 1rem;
    background-color: greenyellow;
  }
</style>

