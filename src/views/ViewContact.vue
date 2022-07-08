<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col">
        <p class="h3 text-success fw-bold">Affichage Contact</p>
        <p class="fst-italic">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolor, et. Reiciendis ab facilis alias tenetur eveniet modi illo illum, incidunt dolorum minus laboriosam, deserunt quaerat totam maiores earum rerum mollitia!!</p>
      </div>
    </div>
  </div>

  <!-- Spinner -->
  <div v-if="loading">
    <div class="container">
      <div class="row">
        <div class="col">
          <Spinner/>
        </div>
      </div>
    </div>
  </div>

  <!-- Error Message -->
  <div v-if="!loading && errorMessage">
    <div class="container mt-3">
      <div class="row">
        <div class="col">
          <p class="h4 text-danger fw-bold">{{errorMessage}}</p>
        </div>
      </div>
    </div>
  </div>

  <div class="container" v-if="!loading && isDone">
    <div class="row">
      <div class="col-md-4">
        <img :src="contact.photo" alt="" class="contact-img-big">
      </div>
      <div class="col-md-6">
        <ul class="list-group">
          <li class="list-group-item">Nom : <span class="fw-bold">{{contact.nom}}</span></li>
          <li class="list-group-item">Email : <span class="fw-bold">{{contact.email}}</span></li>
          <li class="list-group-item">Téléphone : <span class="fw-bold">{{contact.telephone}}</span></li>
          <li class="list-group-item">Compagnie : <span class="fw-bold">{{contact.compagnie}}</span></li>
          <li class="list-group-item">Titre : <span class="fw-bold">{{contact.titre}}</span></li>
          <li class="list-group-item">Groupe : <span class="fw-bold">{{group.nom}}</span></li>
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
import { ContactService } from '@/services/ContactService'
import Spinner from '@/components/Spinner.vue';
  export default {
    name: "ViewContact",
    components: {Spinner},
    data: function () {
        return {
            contactId: this.$route.params.contactId,
            loading: false,
            contact: {},
            errorMessage: null,
            group: {}
        };
    },
    created: async function () {
        try {
            this.loading = true;
            let response = await ContactService.getContact(this.contactId);
            let groupResponse = await ContactService.getGroup(response.data);
            this.contact = response.data;
            this.group = groupResponse.data;
            this.loading = false;
        }
        catch (error) {
            this.errorMessage = error;
            this.loading = false;
        }
    },
    methods: {
      isDone: function () {
        return Object.keys(this.contact).length > 0 && Object.keys(this.group).length > 0;
      }
    }
}
</script>

<style scoped>
  
</style>