<script setup>
import { Head, Link, router, useForm } from "@inertiajs/vue3";

defineProps({
  auth: {
    type: Object,
    required: true,
  },
  logo: {
    type: String,
    required: true,
  },
  image: {
    type: String,
    required: true,
  },
});

const form = useForm({
  email: "",
  password: "",
});

const submit = () => {
  form.post("login");
};
</script>

<template>
  <Head title="Welcome" />
  <v-app>
    <v-app-bar flat class="py-5">
      <v-container class="d-flex align-center">
        <h2 style="color: #1f6e8c">
          <span style="background-color: #1f6e8c" class="pa-2 text-white rounded-lg"
            >Alumni</span
          >
          Tracking
        </h2>
        <v-spacer></v-spacer>
        <v-btn
          class="font-weight-medium text-capitalize mr-3"
          color="#0E2954"
          rounded
          variant="text"
          size="large"
          @click="router.get(route('register'))"
          >Connect With Us</v-btn
        >
        <v-btn
          class="font-weight-medium text-capitalize"
          color="#0E2954"
          rounded
          variant="outlined"
          size="large"
          @click="router.get(route('login'))"
          >Sign In</v-btn
        >
      </v-container>
    </v-app-bar>
    <v-main>
      <v-container class="py-15">
        <v-row class="d-flex">
          <v-col cols="6">
            <h1
              class="mb-15 text-grey-darken-3"
              style="line-height: 1.5; font-family: 'Roboto', sans-serif; font-size: 45px"
            >
              Reconnect, Engage, Thrive! <br />
              Your Alma Mater Awaits
            </h1>
            <v-img :src="image"></v-img>
          </v-col>
          <v-spacer></v-spacer>
          <v-col cols="5" class="d-flex justify-center flex-column">
            <h1 class="text-center mb-5" style="color: #1f6e8c">
              Log in to your account.
            </h1>
            <v-card class="pa-5 rounded-lg" flat>
              <v-form @submit.prevent="submit">
                <label class="font-weight-medium text-grey-darken-2" for="email"
                  >Email Address</label
                >
                <v-text-field
                  type="email"
                  :error-messages="form.errors.email"
                  v-model="form.email"
                  single-line
                  class="mt-2"
                  id="email"
                  label="joshua@arellanites.edu"
                  variant="outlined"
                  color="#1F6E8C"
                ></v-text-field>
                <label class="font-weight-medium text-grey-darken-2" for="password"
                  >Password</label
                >
                <v-text-field
                  :error-messages="form.errors.password"
                  v-model="form.password"
                  single-line
                  class="mt-2"
                  id="password"
                  label="*********"
                  variant="outlined"
                  color="#1F6E8C"
                  type="password"
                ></v-text-field>
                <v-card-actions class="px-0 d-flex flex-column">
                  <v-btn
                    type="submit"
                    class="text-capitalize"
                    variant="outlined"
                    color="#1F6E8C"
                    rounded
                    size="x-large"
                    block
                    >Log in</v-btn
                  >
                </v-card-actions>
              </v-form>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<style></style>
