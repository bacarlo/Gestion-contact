<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col">
        <p class="h3 text-success fw-bold">Ajout Contact</p>
        <p class="fst-italic">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aut odio praesentium expedita iusto velit temporibus soluta dolorem cupiditate, autem numquam, excepturi veniam inventore ipsa voluptatibus libero quae labore dolores magnam.</p>
      </div>
    </div>
  </div>

  <div class="container mt-3">
    <div class="row">
      <div class="col-md-4">
        <form action="" @submit.prevent="submitCreate()">
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
            <input type="submit" class="btn btn-success" value="Créer">
          </div>
        </form>
      </div>
      <div class="col-md-4">
        <img :src="contact.photo" alt="" class="contact-img">
      </div>
    </div>
  </div>
</template>

<script>
import { ContactService } from '@/services/ContactService'
  export default {
    name: "AddContact",
    data: function () {
      return {
        contact: {
          nom : '',
          photo: '',
          email: '',
          telephone: '',
          compagnie: '',
          titre: '',
          groupId: ''
        },
        groups : []
      }
    },

    created : async function () {
      try {
        let response = await ContactService.getAllGroups();
        this.groups = response.data;
      }
      catch (error) {
        console.log(error);
      }
    },

    methods: {
      submitCreate: async function () {
        try{
          let response = await ContactService.createContact(this.contact);
          if(response){
            return this.$router.push('/');
          }
          else {
            return this.$router.push('/contacts/add');
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