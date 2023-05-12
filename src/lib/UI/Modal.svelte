<script>
    export let visible = false;
    let title = '';
</script>

{#if visible}
    <div class="backdrop">
        <div class="modal">
            <div class="modalContent">
                <header>
                    <input bind:value={title} type="text" placeholder="Title here">
                </header>
                <main>
                    <h3>Start</h3>
                    <p><slot name="start"/></p>
                    
                    <h3>End</h3>
                    <p><slot name="end"/></p>
                    
                    <h3>Tech</h3>
                    <p><slot name="tech"/></p>
                </main>
            </div>
        </div>
    </div>
{/if}

<style>
    .backdrop {
        background-color: #00000078;
        width: 100%;
        height: 100%;
        z-index: 90;

        position: fixed;
        top: 0;
        left: 0;
    }

    .modal {
        position: relative;
        z-index: 100;
        background-color: #fff;
        border-radius: 0.25rem;
        width: 350px;
        box-shadow: 0 2px 8px #00000061;

        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -100%);
    }

    .modal h3 {
        font-weight: bold;
        font-size: 0.75rem;
    }

    .modal p {
        margin-bottom: 1rem;
    }

    .modal input {
        width: 100%;
        background-color: transparent;
        outline: none;
        color: #fff;
        caret-color: #fff;
    }

    .modal input:active,
    .modal input:focus {
        border-bottom: 2px solid #fff;
    }

    .modal input::placeholder {
        color: #ffffff94;
    }

    header {
        background-color: #26B0E4;
        border-radius: 0.25rem 0.25rem 0 0;
        padding: 1rem;
    }

    main {
        padding: 1rem;
    }
</style>