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
        <form @submit.prevent="updateSubmit()">
          <div class="mb-2">
            <input required v-model="contact.nom" type="text" class="form-control" placeholder="Nom">
          </div>
          <div class="mb-2">
            <input required v-model="contact.photo" type="text" class="form-control" placeholder="URL Photo">
          </div>
          <div class="mb-2">
            <input required v-model="contact.email" type="email" class="form-control" placeholder="Email">
          </div>
          <div class="mb-2">
            <input required v-model="contact.telephone" type="number" class="form-control" placeholder="Téléphone">
          </div>
          <div class="mb-2">
            <input required v-model="contact.compagnie" type="text" class="form-control" placeholder="Compagnie">
          </div>
          <div class="mb-2">
            <input required v-model="contact.titre" type="text" class="form-control" placeholder="Titre">
          </div>
          <div class="mb-2">
            <select required v-model="contact.groupId" class="form-control" v-if="groups.length > 0">
              <option value="">Sélectioner un groupe</option>
              <option :value="group.id" v-for="group of groups" :key="group.id">{{group.nom}}</option>
            </select>
          </div>
          <div class="mb-2">
            <input type="submit" class="btn btn-success" value="Mettre à jour">
          </div>
        </form>
      </div>
      <div class="col-md-4">
        <img :src="contact.photo" alt="" class="contact-img">
      </div>
    </div>
  </div>
  <pre>{{contact}}</pre>
</template>

<script>
import { ContactService } from '@/services/ContactService';
  export default {
    name: "EditContact",
    data: function() {
      return {
        contactId: this.$route.params.contactId,
        loading: false,
        contact: {
          nom : '',
          photo: '',
          email: '',
          telephone: '',
          compagnie: '',
          titre: '',
          groupId: ''
        },
        errorMessage: null,
        groups: []
      }
    },

    created: async function() {
      try{
        this.loading = true ;
        let response = await ContactService.getContact(this.contactId);
        let groupResponse = await ContactService.getAllGroups()
        this.contact = response.data;
        this.groups = groupResponse.data;
        this.loading = false;
      }
      catch (error) {
        this.errorMessage = error;
        this.loading = false;
      }
    },

    methods: {
      updateSubmit: async function() {
        try{
          let response = await ContactService.updateContact(this.contact, this.contactId);
          if(response){
            return this.$router.push('/');
          }
          else {
            return this.$router.push(`/contacts/edit/${this.contactId}`);
          }
        }
        catch(error){
          console.log(error);
        }
      }
    }
  }
</script>

<style scoped>
  
</style>