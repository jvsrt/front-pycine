<script>
    
    let promise = getUsers();
    async function getUsers() {
        const res = await fetch(
            `http://localhost:8000/user`
        );
        const text = await res.json();
        if (res.ok) {
            return text;
        } else {throw new Error(text); }
    };


</script>
    
    
    
    {#await promise},
    {:then users}
    

    <div class="table">
    <table class="border-collapse border border-slate-400">
        <thread>
            <tr>
                <th class="border border-slate-300">id</th>
                <th class="border border-slate-300">Nome</th>
                <th class="border border-slate-300">email</th>
            </tr>
        </thread>

        <tbody>
        {#each users as u }
    
        <tr> 
            <td class="border border-slate-300">{u.id}</td>
            <td class="border border-slate-300">{u.name}</td>
            <td class="border border-slate-300">{u.email}</td>
            
        </tr>
        {/each}

        
        </tbody>
    
    
    </table>
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