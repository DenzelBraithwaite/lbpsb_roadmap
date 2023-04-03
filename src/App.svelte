<script lang="ts">
  import { onMount } from 'svelte';
  import Navbar from './lib/UI/Navbar.svelte';

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
    let calendarEl: HTMLElement = document.getElementById('calendar')!;
  
    let calendar = new Calendar(calendarEl, {
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
        left: 'prev,next today',
        center: 'title',
        right: 'dayGridMonth,timeGridWeek,listWeek'
      },
      dateClick: function(info) {
        // Do something more meaningful here
        // let dateString: String = info.dateStr;
        // alert(`You clicked on: ${dateString}`)
        // alert('Coordinates: ' + info.jsEvent.pageX + ',' + info.jsEvent.pageY);
        // alert('Current view: ' + info.view.type);
        // change the day's background color just for fun
        info.dayEl.style.backgroundColor = 'pink';
    }});

    calendar.render();
  });

</script>
<Navbar />
<div id="calendar"></div>

<style>
  #calendar {
    margin: 0 auto;
    padding-top: 120px;
    height: 80vh;
    width: 80vw;
  }
</style>

