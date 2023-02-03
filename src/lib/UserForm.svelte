<script>
    function refreshPage(){
        window.location.reload();
    } 
async function addUser(){

    let data = {
        // @ts-ignore
        id: document.getElementById("id").value,
        // @ts-ignore
        name: document.getElementById("name").value,
        // @ts-ignore
        email: document.getElementById("email").value,
        // @ts-ignore
        password: document.getElementById("password").value
} 
    
    const res = await fetch(`http://localhost:8000/user`,{
        method: 'POST',
        headers: {
           'Content-Type': 'application/json'
        },
        body: JSON.stringify(data)
    })
        const text = await res.json();
        console.log(text)
        if (res.ok) {
            return text;
        } else {throw new Error(text); }

}

</script>

<div class="table">
<div id="container-users">
    <div class="acoes">
        
        <input type="hidden" class="input" name="id" id="id">
        <input type="email" class="input" placeholder="email" id="email" name="email" >
        <input type="text" class="input" placeholder="name" id="name" name="name" >
        <input type="password" class="input" placeholder="password" id="password" name="password">

        <button class="button" on:click={addUser}
        on:click={refreshPage}>
        Criar Usuario
        </button>
    </div>
</div>
</div>

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

    .input{
        margin-left: 12px;
    }
</style>