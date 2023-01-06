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
        <thread>
            <tr>
                <th>id</th>
                <th>Nome</th>
                <th>email</th>
            </tr>
        </thread>

        <tbody>
        {#each users as u }
    
        <tr>
            <td>{u.id}</td>
            <td>{u.name}</td>
            <td>{u.email}</td>
            
        </tr>

        {/each}
        </tbody>
        
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