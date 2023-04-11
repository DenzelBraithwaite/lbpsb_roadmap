<script lang="ts">
    import { createEventDispatcher } from 'svelte';

    export let filePath;

    $: tech = '';
    $: fName = tech.split(' ')[0];
    $: lName = tech.split(' ')[1] || '';
    $: title = '';
    $: description = '';
    $: startDate = '';
    $: endDate = '';

    const techs = [
        {
            'id': '1',
            'firstName': 'denzel',
            'lastName': 'braithwaite',
            'email': 'denzel.braithwaite@lbpearson.com',
            'username': 'd.braithwaite',
            'role': 'devloper'
        },
        {
            'id': '2',
            'firstName': 'jeffrey',
            'lastName': 'hammond',
            'email': 'jeffrey.hammond@lbpearson.com',
            'username': 'j.hammond',
            'role': 'technician'
        },
        {
            'id': '3',
            'firstName': 'steven',
            'lastName': 'lacroix',
            'email': 'steven.lacroix@lbpearson.com',
            'username': 's.lacroix',
            'role': 'devloper'
        },
        {
            'id': '4',
            'firstName': 'mario',
            'lastName': 'mario', // His last name is actually Mario
            'email': 'mario.mario@lbpearson.com',
            'username': 'm.mario',
            'role': 'plumber'
        },
        {
            'id': '5',
            'firstName': 'lester',
            'lastName': 'pearson',
            'email': 'lester.pearson@lbpearson.com',
            'username': 'l.pearson',
            'role': 'prime minister'
        },
    ];

    const createEvent = createEventDispatcher();

    function addProjectHandler() {
        createEvent('addProject', {
            'title': title,
            'start': startDate,
            'end': endDate,
        })
    }
</script>

<!-- For Debugging-->
<p><span class="font-bold">First name: </span>{fName}</p>
<p><span class="font-bold">Last name: </span>{lName}</p>
<p><span class="font-bold">tech: </span>{tech}</p>
<p><span class="font-bold">Title: </span>{title}</p>
<p><span class="font-bold">Description: </span> {description}</p>
<p><span class="font-bold">Start: </span> {startDate}</p>
<p><span class="font-bold">End: </span> {endDate}</p>

<form on:submit|preventDefault={addProjectHandler} class="mx-auto border-t-2 border-cyan-800 rounded" action="{filePath}">
<h1 class="text-center text-2xl ">Create an Event</h1>
<div class="form-control">
    <input bind:value={title} id="title" name="title" type="text" placeholder="Title" class="border-b">
    <input bind:value={description} id="title" name="title" type="text" placeholder="Description" class="border-b">
    <div class="border-b py-2">
            <label for="tech" class="">Choose Technician</label>
            <select bind:value={tech} name="tech" id="tech" class="border rounded">
                {#each techs as tech}
                    <option value="{tech['firstName'] + ' ' + tech['lastName']}">{tech['firstName'] + ' ' + tech['lastName']}</option>
                {/each}
            </select>
        </div>
    <input bind:value={startDate} id="title" name="title" type="date" placeholder="Start" class="border-b">
    <input bind:value={endDate} id="title" name="title" type="date" placeholder="End" class="border-b">
    <button type="submit" class="mx-auto block text-white bg-cyan-800 rounded px-4 py-2 w-full hover:bg-cyan-700">Add</button>
</div>
</form>

<style>


form {
    width: 50%;
    box-shadow: 0 2px 8px #00000018;
    padding: 1rem 0.5rem;
}


input {
    width: 100%;
    margin-top: 1rem;
}

input:focus {
    outline: none;
    border-bottom: 2px solid #21657cb9;
}

input:last-of-type {
    margin-bottom: 2rem;
}

</style>
  
  