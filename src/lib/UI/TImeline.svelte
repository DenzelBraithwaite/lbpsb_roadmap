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

    // Props
    export let employees = [];

    let timeline;
    onMount(() => {
        const timelineEl: HTMLElement = document.getElementById('timeline')!;

        timeline = new Calendar(timelineEl, {
            // schedulerLicenseKey: '0478426686-fcs-1616090302',
            schedulerLicenseKey: 'CC-Attribution-NonCommercial-NoDerivatives', // Trial version
            // aspectRatio: 1.5,
            height: 650,
            plugins: [ resourceTimelinePlugin ],
            initialView: 'resourceTimeline',
            resources: employees,
            headerToolbar: {
                left: 'prev,today,next',
                center: 'title',
                right: 'timelineDay,timelineWeek,timelineMonth,timelineYear'
            },
            events: [],
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
</style>