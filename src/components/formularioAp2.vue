<template>
    <div id="app" class="form-container">

      <div class="formularioAp2">

        <h2> FORMULÁRIO </h2>

        <div class="form-group">
          <label for="name">Nome completo:</label> 
          <input type="text" id="name" placeholder="Insira seu Nome aqui" v-model="name" :class="{ 'is-invalid': !nameValid }"/> 
        </div>

        <div class="form-group">
          <label for="email">Endereço de e-mail:</label> 
          <input type="email" id="email" placeholder="Insira seu Email aqui" v-model="email" :class="{ 'is-invalid': !emailValid }"/> 
        </div>

        <div class="form-group">
          <label for="age">Idade:</label> 
          <input type="number" id="age" placeholder="insira sua Idade aqui" v-model="age" :class="{ 'is-invalid': !ageValid }"/> 
        </div>

        <div class="form-group">
          <label for="description">Uma Breve Descrição de si mesmo:</label> 
          <textarea id="description" placeholder="Insira sua Descrição aqui" v-model="description" :class="{ 'is-invalid': !descriptionValid }"></textarea>
        </div>

        <div class="form-buttons">
          <button type="button" @click="validateAndSubmitForm" :disabled="formSubmitted" class="btn btn-primary"> <strong>{{ formSubmitted ? 'Enviado' : 'Enviar' }}</strong>
          </button>
          <button type="button" @click="clearForm" class="btn btn-secondary"> <strong>Limpar</strong> </button>
        </div>

      </div>
  
      <div class="submitted-data" v-if="formSubmitted">
        <h3> Dados do formulário </h3>
        <ul>
          <strong>Nome:</strong> {{ submittedData.name }} <br>
          <strong>E-mail:</strong> {{ submittedData.email }} <br>
          <strong>Idade:</strong> {{ submittedData.age }} <br>
          <strong>Descrição:</strong> {{ submittedData.description }} <br>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: "",
        email: "",
        age: null,
        description: "",
        nameValid: true,
        emailValid: true,
        ageValid: true,
        descriptionValid: true,
        formSubmitted: false,
        submittedData: {
          name: "",
          email: "",
          age: null,
          description: "",
        },
      };
    },
    methods: {
      validateAndSubmitForm() {
        this.nameValid = !!this.name;
        this.emailValid = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(this.email); 
        this.ageValid = !isNaN(this.age) && this.age > 0;
        this.descriptionValid = !!this.description;
  
        if (this.nameValid && this.emailValid && this.ageValid && this.descriptionValid) {
          this.submitForm();
        } else {
          alert("Por favor, preencha todos os campos corretamente.");
        }
      },
      submitForm() {
        const userData = {
          name: this.name,
          email: this.email,
          age: this.age,
          description: this.description,
        };
        this.submittedData = userData;
        this.formSubmitted = true;
      },
      clearForm() {
        this.name = "";
        this.email = "";
        this.age = null;
        this.description = "";
        this.nameValid = true;
        this.emailValid = true;
        this.ageValid = true;
        this.descriptionValid = true;
        this.formSubmitted = false;
        this.submittedData = {
          name: "",
          email: "",
          age: null,
          description: "",
        };
      },
    },
  };
  </script>
  
  <style scoped>
  *{
    padding: 0;
    margin: 0;
    border: 0;
  }

  .formularioAp2 {
    align-items: center;
    display: flex;
    flex-direction: column;
    width: 70vh;
    height: 80vh;
    background-color: #ffffff;
  }

  h2 {
    color: #000000;
    align-items: center;
    text-align: center;
    margin-top: 10px;
    margin-bottom: 40px;
  }
  
  h3 {
    color: #000000;
  }

  .form-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items:center;
    height: 90vh;
    width: 500px;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }
  
  .form {
    max-width: 400px;
    width: 100%;
    padding: 40px;
    border-radius: 16px;
    box-shadow: 0 0 10px #E54A59;
  }
  
  .form-group {
    align-items: center;
    margin-bottom: 20px;
    width: 100%;
    display: flex;
    flex-direction: column;
  }
  
  label {
    font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin-bottom: 8px;
  }
  
  input {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    width: 400px;
    height: 25px;
    border: 1px solid #2b2b2b;
    border-radius: 4px;
  }
  
  textarea {
    border: 1px solid #2b2b2b;
    resize: both; 
    overflow: auto;
    width: 400px; 
    min-height: 50px;
    min-width: 200px; 
    max-width: 100%; 
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    border-radius: 4px;
    border-color:#2b2b2b;
  }
  
  .form-control {
    width: 100%;
    padding: 10px;
    font-size: 14px;
    border: 1px solid #ddd;
    border-radius: 4px;
    box-sizing: border-box;
    position: center;
  }
  
  button {
    width: 48%;
    padding: 12px;
    font-size: 16px;
    margin-right: 4%;
    margin-bottom: 10px;
    cursor: pointer;
    position: center;
    border-radius: 4px;
    background-color: #45a049;
  }
  
  .form-buttons {
    display: flex;
    justify-content: space-between;
  }
  
  strong{
    color: black;
  }
  
  .submitted-data {
    margin-top: 10px;
    text-align: left;
    padding: 20px;
    border: 1px solid green;
    border-radius: 8px;
    width: auto;
    box-shadow:#e54a59;
  }
  
  .is-invalid {
    border: 1px solid red;
  }
  </style>