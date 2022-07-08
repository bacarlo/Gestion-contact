<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col">
        <p class="h3 text-success fw-bold">Modifier Contact</p>
        <p class="fst-italic">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Cumque officia accusamus iure voluptatum, assumenda porro voluptates consectetur eum, soluta tempore enim quasi nulla ducimus impedit. Tenetur provident animi dolorum asperiores!</p>
      </div>
    </div>
  </div>
  <div class="container mt-3">
    <div class="row">
      <div class="col-md-4">
        <form action="">
          <div class="mb-2">
            <input type="text" class="form-control" placeholder="Nom">
          </div>
          <div class="mb-2">
            <input type="text" class="form-control" placeholder="URL Photo">
          </div>
          <div class="mb-2">
            <input type="email" class="form-control" placeholder="Email">
          </div>
          <div class="mb-2">
            <input type="number" class="form-control" placeholder="Téléphone">
          </div>
          <div class="mb-2">
            <input type="text" class="form-control" placeholder="Compagnie">
          </div>
          <div class="mb-2">
            <input type="text" class="form-control" placeholder="Titre">
          </div>
          <div class="mb-2">
            <select class="form-control">
              <option value="">Sélectioner un groupe</option>
            </select>
          </div>
          <div class="mb-2">
            <input type="submit" class="btn btn-success" value="Mettre à jour">
          </div>
        </form>
      </div>
      <div class="col-md-4">
        <img src="https://cdn-icons-png.flaticon.com/512/219/219986.png" alt="" class="contact-img">
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "EditContact"
  }
</script>

<style scoped>
  
</style>