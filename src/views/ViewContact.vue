<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col">
        <p class="h3 text-success fw-bold">Affichage Contact</p>
        <p class="fst-italic">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolor, et. Reiciendis ab facilis alias tenetur eveniet modi illo illum, incidunt dolorum minus laboriosam, deserunt quaerat totam maiores earum rerum mollitia!!</p>
      </div>
    </div>
  </div>
  <div class="container">
    <div class="row">
      <div class="col-md-4">
        <img src="https://cdn-icons-png.flaticon.com/512/219/219986.png" alt="" class="contact-img-big">
      </div>
      <div class="col-md-6">
        <ul class="list-group">
          <li class="list-group-item">Nom : <span class="fw-bold">Nom</span></li>
          <li class="list-group-item">Email : <span class="fw-bold">Email</span></li>
          <li class="list-group-item">Téléphone : <span class="fw-bold">Téléphone</span></li>
          <li class="list-group-item">Compagnie : <span class="fw-bold">Compagnie</span></li>
          <li class="list-group-item">Titre : <span class="fw-bold">Titre</span></li>
          <li class="list-group-item">Groupe : <span class="fw-bold">Groupe</span></li>
        </ul>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col">
        <router-link to="/" class="btn btn-success"><i class="fa fa-arrow-circle-left"></i> Retour</router-link>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "ViewContact"
  }
</script>

<style scoped>
  
</style>