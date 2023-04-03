<script lang="ts">
  import { onMount } from 'svelte';
  import Navbar from './lib/UI/Navbar.svelte';

  // Full Calendar Plugins
  import { Calendar } from '@fullcalendar/core';
  import dayGridPlugin from '@fullcalendar/daygrid';
  import timeGridPlugin from '@fullcalendar/timegrid';
  import listPlugin from '@fullcalendar/list';

  // Unused right now
  // import InteractionPlugin from '@fullcalendar/interaction';
  // import MultiMonthPlugin from '@fullcalendar/multimonth';
  // import ScrollGridPlugin from '@fullcalendar/scrollgrid';
  
  onMount(() => {
    let calendarEl: HTMLElement = document.getElementById('calendar')!;
  
    let calendar = new Calendar(calendarEl, {
      plugins: [ dayGridPlugin, timeGridPlugin, listPlugin ],
      initialView: 'dayGridMonth',
      headerToolbar: {
        left: 'prev,next today',
        center: 'title',
        right: 'dayGridMonth,timeGridWeek,listWeek'
      }
    });

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

