<script setup>
import { ref } from 'vue';

const form = ref({
  access_key: "YOUR_ACCESS_KEY_HERE",
  subject: "Contact Submission from Finger-Fun",
  name: "",
  email: "",
  message: "",

});

const result = ref("");
const status = ref("");

const submitForm = async () => {
  result.value = "Please wait...";
  try {
    const response = await $fetch('https://api.web3forms.com/submit', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: form.value,
    });

    console.log(response); // You can remove this line if you don't need it

    result.value = response.message;

    if (response.status === 200) {
      status.value = "success";
    } else {
      console.log(response); // Log for debugging, can be removed
      status.value = "error";
    }
  } catch (error) {
    console.log(error); // Log for debugging, can be removed
    status.value = "error";
    result.value = "Something went wrong!";
  } finally {
    // Reset form after submission
    form.value.name = "";
    form.value.email = "";
    form.value.message = "";

    // Clear result and status after 5 seconds
    setTimeout(() => {
      result.value = "";
      status.value = "";
    }, 5000);
  }
};
</script>

<template>
  <main>
    <section>
    <div class="container my-8">
      <div class="grid place-content-center">
        <p class="text-center text-sm">Message Us</p>
        <h2 class="text-lg font-semibold md:text-4xl">Get in touch</h2>
      </div>
      <div class="my-8">
        <form @submit.prevent="submitForm">
          <div class="my-2"><label for="name">Name </label><input class="px-2 py-1" type="text" name="name" v-model="form.name"/></div>
          <div class="my-2"><label>Email </label><input class="px-2 py-1" type="email" name="email"  v-model="form.email"/></div>
          <div><label>Message</label><textarea name="message" v-model="form.message"></textarea></div>
          
          <button class="btn-primary px-6 py-3 text-white bg-green-500 rounded-xl" type="submit">Send Message</button>
        </form>
      </div>
    </div>
    </section>
  </main>
</template>
