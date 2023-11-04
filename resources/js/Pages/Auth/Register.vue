<script setup>
import { Head, Link, useForm, router } from "@inertiajs/vue3";

defineProps({
  canResetPassword: {
    type: Boolean,
  },
  status: {
    type: String,
  },
});

const form = useForm({
  email: "",
  password: "",
  password_confirmation: "",
  name: "",
  student_number: "",
  special_message: "",
});

const submit = () => {
  form.post("/register");
};
</script>

<template>
  <Head title="Sign in"></Head>
  <v-app>
    <v-app-bar flat class="py-5 px-15">
      <h3 style="color: #1f6e8c; cursor: pointer" @click="router.get('/')">
        <span style="background-color: #1f6e8c" class="pa-2 text-white rounded-lg"
          >Alumni</span
        >
        Tracking
      </h3>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-row justify="center">
          <v-col cols="7" class="pt-10">
            <h1 class="text-center mb-5" style="color: #1f6e8c">Connect with us now</h1>
            <v-card class="pa-5 rounded-lg" flat>
              <v-alert
                type="error"
                variant="tonal"
                class="mb-2"
                v-if="form.errors.special_message"
              >
                {{ form.errors.special_message }}
              </v-alert>
              <v-form @submit.prevent="submit">
                <label class="font-weight-medium text-grey-darken-2" for="name"
                  >Name</label
                >
                <v-text-field
                  type="text"
                  :error-messages="form.errors.name"
                  v-model="form.name"
                  single-line
                  class="mt-2"
                  id="name"
                  label="Joshua Sotto, John Doe, Jane etc"
                  variant="outlined"
                  color="#1F6E8C"
                ></v-text-field>
                <label class="font-weight-medium text-grey-darken-2" for="student_number"
                  >Student number</label
                >
                <v-text-field
                  type="text"
                  :error-messages="form.errors.student_number"
                  v-model="form.student_number"
                  single-line
                  class="mt-2"
                  id="student_number"
                  label="10-1010"
                  variant="outlined"
                  color="#1F6E8C"
                ></v-text-field>
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
                <v-row>
                  <v-col>
                    <label
                      class="font-weight-medium text-grey-darken-2"
                      for="password-confirmation"
                      >Confirmation Password</label
                    >
                    <v-text-field
                      :error-messages="form.errors.password_confirmation"
                      v-model="form.password_confirmation"
                      single-line
                      class="mt-2"
                      id="password-confirmation"
                      label="*********"
                      variant="outlined"
                      color="#1F6E8C"
                      type="password"
                    ></v-text-field>
                  </v-col>
                  <v-col>
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
                  </v-col>
                </v-row>
                <v-card-actions class="px-0 d-flex flex-column">
                  <v-btn
                    type="submit"
                    class="text-capitalize"
                    variant="outlined"
                    color="#1F6E8C"
                    rounded
                    size="x-large"
                    block
                    >Connect</v-btn
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
