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
  remember: false,
});

const submit = () => {
  form.post(route("login"), {
    onFinish: () => form.reset("password"),
  });
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
          <v-col cols="6" class="pt-15">
            <h1 class="text-center mb-5" style="color: #1f6e8c">
              Welcome back, Log in to your account.
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
