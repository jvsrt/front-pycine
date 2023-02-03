<script>
    function refreshPage(){
        window.location.reload();
    } 

    async function deleteUser(){
    
        let data = {
            // @ts-ignore
            id: document.getElementById("deleteid").value,
    } 
        
        const res = await fetch(`http://localhost:8000/user/${data.id}`,{
            method: 'DELETE',
            headers: {
               'Content-Type': 'application/json'
            },
            body: JSON.stringify(data)
        })
            const text = await res.json();
            console.log(text)
            if (res.ok) {
                window.location.reload();
                return text;
            } else {throw new Error(text); }
    
    }
    
    </script>
    
    
    <div class="table">
        <div class="acoes">
            <input type="text" placeholder="id" name="id" id="deleteid">
    
            <button class="button" 
            on:click={deleteUser}
            on:click={refreshPage}>
            Delete User
            </button>
        </div>
    </div>

    <style>
        .button{
        background-color: white;
        color: red;
        border-color: silver;
        box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;;
        margin-left: 12px;
    }

    .table{
            display: flex;
            position: absolute;
            width:fit-content;
            grid-template-columns: 1fr 1fr 1fr 1fr;
            border: 1px solid #ccc;
            padding: 6px;
            align-self: center;
            align-content: center;
            justify-content: center;
    }

    .acoes{
        padding: 16px;
    }

    .input{
        margin-left: 12px;
    }
    </style>