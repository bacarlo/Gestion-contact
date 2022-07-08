<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col">
        <p class="h3 text-success fw-bold">Gestion de Contact
          <router-link to="/contacts/add" class="btn btn-success btn-sm" ><i class="fa fa-plus-circle"></i>New</router-link>
        </p>
        <p class="fst-italic">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Sapiente soluta impedit, adipisci minima corrupti expedita deserunt ab harum hic tenetur rerum vero quasi consectetur quidem magni exercitationem quia officiis aperiam.</p>
        <form action="">
          <div class="row">
            <div class="col-md-6">
              <div class="row">
                <div class="col">
                  <input type="text" class="form-control" placeholder="Rechercher nom" >
                </div>
                <div class="col">
                  <input type="submit" class="btn btn-outline-dark" value="Rechercher">
                </div>
              </div>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
  <div class="container mt-3">
    <div class="row">
      <div class="col-md-6">
        <div class="card my-2 list-group-item-success shadow-lg">
          <div class="card-body">
            <div class="row align-items-center">
              <div class="col-sm-4">
                <img src="https://cdn-icons-png.flaticon.com/512/219/219986.png" alt="" class="contact-img">
              </div>
              <div class="col-sm-7">
                <ul class="list-group">
                  <li class="list-group-item">Nom : <span class="fw-bold">Nom</span></li>
                  <li class="list-group-item">Email : <span class="fw-bold">Email</span></li>
                  <li class="list-group-item">Téléphone : <span class="fw-bold">Téléphone</span></li>
                </ul>
              </div>
              <div class="col-sm-1 d-flex flex-column justify-content-center align-items-center">
                <router-link to="/contacts/view/:contactId" class="btn btn-warning my-1">
                  <i class="fa fa-eye"></i>
                </router-link>
                <router-link to="/contacts/edit/:contactId" class="btn btn-primary my-1">
                  <i class="fa fa-pen"></i>
                </router-link>
                <button class="btn btn-danger my-1">
                  <i class="fa fa-trash"></i>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "ContactManager"
  }
</script>

<style scoped>

</style>