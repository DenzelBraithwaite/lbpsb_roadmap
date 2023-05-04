<script lang="ts">
    // Svelte hooks
    import { onMount } from 'svelte';

    // FullCalendar plugins & hooks
    import { Calendar } from '@fullcalendar/core';
    import dayGridPlugin from '@fullcalendar/daygrid';
    import timeGridPlugin from '@fullcalendar/timegrid';
    import listPlugin from '@fullcalendar/list';

    // Premium FullCalendar features
    import resourceTimelinePlugin from '@fullcalendar/resource-timeline';

    onMount(() => {
        console.log('yes mounted')

        const timelineEl: HTMLElement = document.getElementById('timeline')!;
        let timeline = new Calendar(timelineEl, {
            schedulerLicenseKey: '0478426686-fcs-1616090302',
            // schedulerLicenseKey: 'CC-Attribution-NonCommercial-NoDerivatives', // Trial version
            plugins: [ resourceTimelinePlugin ],
            initialView: 'resourceTimeline',
            // resources: [],
            headerToolbar: {
                left: 'prev,next today',
                center: 'title',
                right: 'timelineDay, timelineWeek, timelineMonth, timelineYear'
            }
        });
        timeline.render();
    });

</script>

<main>
    <div id="timeline"></div>
</main>

<style>
    main {
        min-height: 50vh;
    }

    #calendar {
        height: 600px;
    }
</style>