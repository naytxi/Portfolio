<template>
    <div class="contact-wrapper">
      <h2 class="contact-title">CONTACT US</h2>
      <form class="contact-form" @submit.prevent="handleSubmit">
        <label>
          Choose your Fairy Godmother
          <select v-model="form.recipient" required>
            <option disabled value="">-- Choose One --</option>
            <option>Flora</option>
            <option>Fauna</option>
            <option>Merriweather</option>
          </select>
        </label>
        <label>
          Name
          <input type="text" v-model="form.name" required />
        </label>
        <label>
          Email
          <input type="email" v-model="form.email" required />
        </label>
        <label>
          Message
          <textarea v-model="form.message" rows="5" required></textarea>
        </label>
        
        <button type="submit">Send Message</button>
      </form>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const form = ref({
    name: '',
    email: '',
    message: '',
    recipient: ''
  });
  
  const handleSubmit = () => {
    alert(`Message sent to ${form.value.recipient}!`);
    form.value = {
      name: '',
      email: '',
      message: '',
      recipient: ''
    };
  };
  </script>
  
  <style scoped>
  .contact-wrapper {
    padding: 1rem 2rem;
    max-width: 800px;
    margin: 0 auto;
  }
  
  .contact-title {
    font-family: "Cinzel", serif;
    font-size: 2.5rem;
    color: #f5ede1;
    margin-bottom: 1rem;
    text-align: center;
  }
  
  .contact-form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  
  label {
    display: flex;
    flex-direction: column;
    font-family: "Playfair Display", serif;
    color: #f5ede1;
    font-size: 1.2rem;
  }
  
  input,
  textarea,
  select {
    padding: 0.8rem;
    border-radius: 8px;
    border: none;
    background-color: #2b2b2b;
    color: #f5ede1;
    font-size: 1rem;
    margin-top: 0.5rem;
  }
  
  input:focus,
  textarea:focus,
  select:focus {
    outline: none;
    box-shadow: 0 0 5px #999;
  }
  
  button {
    align-self: flex-end;
    padding: 0.8rem 1.5rem;
    font-family: "Cinzel", serif;
    font-size: 1.5rem;
    background-color: #f5ede1;
    color: #1e1e1e;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: transform 0.3s ease, background-color 0.3s ease;
  }
  
  button:hover {
    transform: scale(1.05);
    background-color: #a8957a;
  }
  </style>
  