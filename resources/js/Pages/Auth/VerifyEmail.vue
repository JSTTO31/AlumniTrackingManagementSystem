<script setup>
import { computed } from "vue";
import { Head, Link, router, useForm } from "@inertiajs/vue3";

const props = defineProps({
  status: {
    type: String,
  },
  auth: {
    type: Object,
    required: true,
  },
});

const form = useForm({});

const submit = () => {
  form.post(route("verification.send"));
};

const verificationLinkSent = computed(() => props.status === "verification-link-sent");
</script>

<template>
  <v-app>
    <Head title="Email Verification" />
    <v-app-bar flat class="py-5 px-15">
      <h3 style="color: #1f6e8c; cursor: pointer" @click="router.get('/')">
        <span style="background-color: #1f6e8c" class="pa-2 text-white rounded-lg"
          >Alumni</span
        >
        Tracking
      </h3>
    </v-app-bar>
    <v-main style="padding-inline: 390px" class="d-flex flex-column">
      <v-avatar variant="tonal" color="#1F6E8C" class="mx-auto mt-15" size="60">
        <v-icon size="30">mdi-email</v-icon>
      </v-avatar>
      <h1 class="text-center mt-10" style="color: #0e2954">Please Verify Your Email</h1>
      <h3
        class="text-center px-14 font-weight-regular"
        style="font-family: 'Poppins' !imporatant"
      >
        You're almost there we send email to <strong>{{ auth.user.email }}</strong>
      </h3>
      <div class="my-5 text-center" style="font-family: 'Poppins' !important">
        Thanks for signing up! Before getting started, could you verify your email address
        by clicking on the link we just emailed to you? If you didn't receive the email,
        we will gladly send you another.
      </div>
      <div>
        <v-alert variant="tonal" type="info" v-if="verificationLinkSent">
          A new verification link has been sent to the email address you provided during
          registration.
        </v-alert>
      </div>

      <form @submit.prevent="submit">
        <div class="d-flex justify-center mt-15">
          <v-btn
            type="submit"
            prepend-icon="mdi-send"
            color="#1F6E8C"
            class="mr-2 text-capitalize"
            :class="{ 'opacity-25': form.processing }"
            :disabled="form.processing"
          >
            Resend Verification Email
          </v-btn>
          <v-btn
            class="text-capitalize"
            prepend-icon="mdi-logout"
            @click="router.post('logout')"
            >Logout</v-btn
          >
        </div>
      </form>
    </v-main>
  </v-app>
</template>
