<script lang="ts">
  
</script>

<form class="mx-auto border-t-2 border-cyan-800 rounded" action="#">
<h1 class="text-center text-2xl ">Create an Event</h1>
<div class="form-control">
    <input id="title" name="title" type="text" placeholder="Title" class="border-b">
    <input id="title" name="title" type="text" placeholder="Description" class="border-b">
    <input id="title" name="title" type="date" placeholder="Start" class="border-b">
    <input id="title" name="title" type="date" placeholder="End" class="border-b">
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
  
  