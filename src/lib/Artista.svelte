<script>
    let promise = getArtistas();
    async function getArtistas() {
        const res = await fetch(
            `http://localhost:8000/artista/name/Arnold`
        );
        const text = await res.json();
        if (res.ok) {
            return text;
        } else {throw new Error(text); }
    }
    function handleClick() {
        promise = getArtistas();
    }
    </script>
    <button on:click={handleClick}>
    
    </button>
    
    <!--
        get from endpoint /genres
        <select>
            <option>Drama</option>
        </select
    -->
    
    {#await promise}
    <p>...waiting</p>
    {:then a}
    
    <div class="table">
        
            
            <!-- <p>{m.id}</p> -->
            <p><img src="{a.profile_path}"/></p>
            <p>{a.id}</p>
            <p>{a.name}</p>
            <p>{a.popularity}</p>
            <!-- TODO: salvar filme como favorito -->
            <p>Save</p>
        
    </div>
    
    {:catch error}
        <p style="color: red">{error.message}</p>
    {/await}
    
    <style>
    .table{
        display: grid;
        
        width: 860px;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        border: 1px solid #ccc;
        padding: 6px;
    }
    </style>