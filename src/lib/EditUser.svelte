<script>
    function refreshPage(){
        window.location.reload();
    }

    let selectId;

    let promise = getUsersID();
    async function getUsersID() {
        const res = await fetch(
            `http://localhost:8000/user`
        );
        const text = await res.json();
        if (res.ok) {
            return text;
        } else {throw new Error(text);}
    };

    async function editUser(){
        
        let data = {
            // @ts-ignore
            id: document.getElementById("edit-id").value,
            // @ts-ignore
            name: document.getElementById("edit-name").value,
            // @ts-ignore
            email: document.getElementById("edit-email").value,
            // @ts-ignore
            password: document.getElementById("edit-password").value
    }
        
        const res = await fetch(`http://localhost:8000/user/${data.id}`,{
            method: 'PUT',
            headers: {
               'Content-Type': 'application/json'
            },
            body: JSON.stringify(data)
        })
            const text = await res.json();
            
            if (res.ok) {
                return text;
            } else {throw new Error(text); }
    
    }
    
    </script>
    
    <br>
    <br>

    {#await promise},
    {:then users}

    <div class="table">
            
            <input type="text" placeholder="ID" id="edit-id" name="edit-id">
            <input type="email" placeholder="email" id="edit-email" name="edit-email" >
            <input type="text" placeholder="name" id="edit-name" name="edit-name" >
            <input type="password" placeholder="password" id="edit-password" name="edit-password" >
    
            <button class="button" on:click={editUser}
            on:click={refreshPage}>
            Edit from ID
            </button>
    </div>

    {:catch error}

        <p style="color: red">{error.message}</p>
    {/await}

<style>
    .button{
        background-color: white;
        color: green;
        border-color: silver;
        box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;;
        margin-left: 12px;
    }

    .table{
            display: flex;
            width: 860px;
            grid-template-columns: 1fr 1fr 1fr 1fr;
            border: 1px solid #ccc;
            padding: 6px;
    }

    .acoes{
        padding: 16px;
    }

</style>