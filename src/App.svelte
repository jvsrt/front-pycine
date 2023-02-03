<script>
  import Movie from './lib/Movie.svelte'

  import Artista from './lib/Artista.svelte'

  import User from './lib/User.svelte'
  import EditUser from './lib/EditUser.svelte'
  import UserForm from './lib/UserForm.svelte'
  import DeleteUser from './lib/DeleteUser.svelte'

</script>

<main>
  <p>Pycine App</p>

  <div class="card">
    

    <UserForm />
  <br>
  <br>
  <br>
    <User />
  <br>
  <br>
  <br>
    <EditUser />
  <br>
  <br>
  <br>
    <DeleteUser/>
  
  </div>




  <!--<div class="card">
    <Artista/>
  </div> -->


  <button>button</button>

</main>

<style>
/* main :global(button){ */
main button{
    color: rgb(255, 0, 179);
}
button{
    color: rgb(78, 65, 74);
}
.card{
  padding-bottom: 400px;
}
</style>