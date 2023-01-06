<script>

async function addUser(){

    let data = {
        name: "asd",
        email: "a@gmail.com", 
        password: "123"
} 
    const res = await fetch(`http://localhost:8000/user`,{
        method: 'POST',
        body: JSON.stringify(data)
    })
        const text = await res.json();
        if (res.ok) {
            return text;
        } else {throw new Error(text); }

}

</script>


<div id="container-users">
    <div id="acoes">
        <input type="email" placeholder="email" id="email" value='email'>
        <input type="text" placeholder="name" id="name" value='name'>
        <input type="password" placeholder="password" id="password" value='password'>

        <button on:click={addUser}>
        Post it 
        </button>
    </div>
    </div>