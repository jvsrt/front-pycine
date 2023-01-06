<script>
  import Movie from './lib/Movie.svelte'

  import Artista from './lib/Artista.svelte'

  import User from './lib/User.svelte'

  import UserForm from './lib/UserForm.svelte'
</script>

<main>
  <p>Pycine App</p>

  <div class="card">
    

    <UserForm />

    <User />
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
</style>