<script lang="ts">
    import { createEventDispatcher } from "svelte";

    // External props
    export let actionUrl;
    export let employees;
    export let formVisible;
    export let fakeId;
    
    $: fName = employeeTitle.split(' ')[0];
    $: lName = employeeTitle.split(' ')[1] || '';
    $: title = '';
    $: employeeTitle = '';
    $: description = '';
    $: startDate = '';
    $: endDate = '';

    let employee;
    
    const createEvent = createEventDispatcher();

    function submitHandler() {
        // Find the right employee
        employee = employees.find((e) => {
            return e.title === employeeTitle;
        });

        createEvent('addEvent', {
            projectId: "p" + fakeId.toString(),
            resourceId: employee.id,
            title: title,
            description: description,
            start: startDate,
            end: endDate,
        })
    };
</script>

{#if formVisible}
    <form on:submit|preventDefault={submitHandler} class="border-t-2 border-cyan-800 rounded" action="{actionUrl}">
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <p on:click class="x-btn absolute top-2 right-2 text-red-700 font-bold cursor-pointer hover:bg-red-700 hover:rounded hover:text-white hover:p-1">X</p>
        <div class="form-wrapper">
            <h1 class="text-center text-2xl ">Add a Project</h1>
            <input bind:value={title} id="title" name="title" type="text" placeholder="Title" class="border-b" />
            <textarea bind:value={description} id="title" name="title" placeholder="Description" class="border-b p-2 my-2 w-full" />
            <div class="py-5">
                <label for="employee" class="">Choose Employee</label>
                <select bind:value={employeeTitle} name="employee-title" id="employee-title" class="border rounded">
                    {#each employees as emp}
                        <option value="{emp['firstName'] + ' ' + emp['lastName']}">{emp['firstName'] + ' ' + emp['lastName']}</option>
                    {/each}
                </select>
            </div>
            <input bind:value={startDate} id="start" name="start" type="date" placeholder="Start" class="border-b" />
            <input bind:value={endDate} id="end" name="end" type="date" placeholder="End" class="border-b" />
        </div>
        <button type="submit" class="mx-auto block text-white bg-cyan-800 rounded px-4 py-2 w-full hover:bg-cyan-700">Add</button>
    </form>
{/if}

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
  
  