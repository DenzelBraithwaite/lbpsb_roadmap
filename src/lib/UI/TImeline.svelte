<script lang="ts">
    // Svelte hooks
    import { onMount } from 'svelte';

    // FullCalendar plugins & hooks
    import { Calendar } from '@fullcalendar/core';
    import dayGridPlugin from '@fullcalendar/daygrid';
    import timeGridPlugin from '@fullcalendar/timegrid';
    import listPlugin from '@fullcalendar/list';

    onMount(() => {
        console.log('yes mounted')

        const calendarEl: HTMLElement = document.getElementById('calendar')!;
        let calendar = new Calendar(calendarEl, {
            plugins: [ dayGridPlugin, timeGridPlugin, listPlugin ],
            initialView: 'dayGridMonth',
            headerToolbar: {
                left: 'prev,next today',
                center: 'title',
                right: 'dayGridMonth,timeGridWeek,listWeek'
            }
        });
    });

</script>

<h1>Hello Girl</h1>

<style>
    h1 {
        color: red;
    }
</style>