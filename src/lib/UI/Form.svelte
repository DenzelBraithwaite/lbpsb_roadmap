<script lang="ts">
    import { createEventDispatcher } from "svelte";

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
    
    function formHandler(event) {
        createEvent('formSubmit', {
            'title': title,
            'start': startDate,
            'end': endDate,
        })
    }
</script>

<form on:submit|preventDefault={formHandler} class="border-t-2 border-cyan-800 rounded" action="{filePath}">
    <p on:click class="x-btn absolute top-2 right-2 text-red-700 font-bold cursor-pointer hover:bg-red-700 hover:rounded hover:text-white hover:p-1">X</p>
    <div class="form-wrapper">
        <h1 class="text-center text-2xl ">Create an Event</h1>
        <input bind:value={title} id="title" name="title" type="text" placeholder="Title" class="border-b" />
        <textarea bind:value={description} id="title" name="title" placeholder="Description" class="border-b p-2 my-2 w-full" />
        <div class="py-5">
            <label for="tech" class="">Choose Technician</label>
            <select bind:value={tech} name="tech" id="tech" class="border rounded">
                {#each techs as tech}
                    <option value="{tech['firstName'] + ' ' + tech['lastName']}">{tech['firstName'] + ' ' + tech['lastName']}</option>
                {/each}
            </select>
        </div>
        <!-- <div class="form-wrapper">
            <label for="" class="bg-cyan-700">All-day?</label>
            <input type="checkbox" />
        </div> -->
        <input bind:value={startDate} id="title" name="title" type="date" placeholder="Start" class="border-b" />
        <input bind:value={endDate} id="title" name="title" type="date" placeholder="End" class="border-b" />
    </div>
    <button type="submit" class="mx-auto block text-white bg-cyan-800 rounded px-4 py-2 w-full hover:bg-cyan-700">Add</button>

    <!-- For Debugging-->
    <!-- <p><span class="font-bold">First name: </span>{fName}</p>
    <p><span class="font-bold">Last name: </span>{lName}</p>
    <p><span class="font-bold">tech: </span>{tech}</p>
    <p><span class="font-bold">Title: </span>{title}</p>
    <p><span class="font-bold">Description: </span> {description}</p>
    <p><span class="font-bold">Start: </span> {startDate}</p>
    <p><span class="font-bold">End: </span> {endDate}</p> -->
</form>

<style>
form {
    position: fixed ;
    z-index: 10;
    right: 0;
    bottom: 0;
    height: 90vh;
    box-shadow: 0 2px 10px #00000018;
    padding: 1rem;
    background-color: #fff;
    
    display: flex;
    flex-flow: column wrap;
    justify-content: space-between;
}

.animate {
    /* Try to make it slide in? */
    transition: transform 0.75s ease-in;
    transform: translateX(-3%);
}

input{
    width: 100%;
    margin-top: 2rem;
}

input:focus {
    outline: none;
    border-bottom: 2px solid #21657cb9;
}

input:last-of-type {
    margin-bottom: 2rem;
}

.x-btn {
    transition: all 0.125s ease-in;
}
</style>
  
  