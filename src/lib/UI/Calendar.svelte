<script lang="ts">
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
  
  onMount(() => {
    const calendarEl: HTMLElement = document.getElementById('calendar')!;
    const calendar = new Calendar(calendarEl, {
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
      events: [
        {
          title: 'test',
          start: '2023-04-10T07:00:00',
          end: '2023-04-12T16:30:00'
        }
      ],
      droppable: true, // This allows things to be dropped onto the calendar
      dateClick: function(info) {
        // Do something more meaningful here
        // let dateString: String = info.dateStr;
        // alert(`You clicked on: ${dateString}`)
        // alert('Coordinates: ' + info.jsEvent.pageX + ',' + info.jsEvent.pageY);
        // alert('Current view: ' + info.view.type);

          if(info.dayEl.style.backgroundColor !== 'rgba(197, 241, 255, 0.525)'){
            // Open a modal with more info about event/project
            info.dayEl.style.backgroundColor = '#c5f1ff86';
            
          } else {
            info.dayEl.style.backgroundColor = 'white';
          }
    }});

    calendar.render();
  });

</script>
<div id="calendar"></div>

<style>
  #calendar {
    margin: 0 auto;
    padding-top: 120px;
    height: 80vh;
    width: 80vw;
  }
</style>

