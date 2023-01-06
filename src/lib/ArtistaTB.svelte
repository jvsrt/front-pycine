<script>
    let promise = getArtistas();
    async function getArtistas() {
        const res = await fetch(
            `http://localhost:8000/artista/name/Arnold`
        );
        
        const text = await res.json();
        if (res.ok) {
            return text;
        } else {
            throw new Error(text);
        }
    }
    function handleClick() {
        promise = getArtistas();
    }
    </script>
    
    <button on:click={handleClick}>
        get artistas
    </button>
    
    {#await promise}
        <p>...waiting</p>
    {:then a}
    
    <table class="border-collapse border border-slate-400">
        <thead>
            <tr>
                <th class="border border-slate-300">id</th>
                <th class="border border-slate-300">title</th>
                <th class="border border-slate-300">genre</th>
            </tr>
        </thead>
        <tbody>

            <tr>
                <td class="border border-slate-300">{a.id}</td>
                <td class="border border-slate-300">{a.name}</td>
                <td class="border border-slate-300">{a.popularity}</td>
            </tr>
            
        </tbody>
    </table>
    
    {:catch error}
        <p style="color: red">{error.message}</p>
    {/await}
    
    <style>
    .data{
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
    }
    </style>