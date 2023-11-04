<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import { Head, usePage } from "@inertiajs/vue3";
import { computed } from "vue";
const $page = usePage();
const user = computed(() => $page.props.auth.user);
</script>

<template>
  <Head title="Home" />

  <AuthenticatedLayout>
    <v-layout class="h-100 w-100">
      <v-navigation-drawer color="transparent" flat floaing class="border-0" width="280">
        <v-card class="d-flex flex-column align-center py-10 rounded-lg">
          <v-avatar size="150" class="rounded-lg">
            <v-img
              src="https://as2.ftcdn.net/v2/jpg/02/44/42/79/1000_F_244427911_aoHHulebtYy4wLpncBBuWqCTNFKolcCB.jpg"
            ></v-img>
          </v-avatar>
          <h3 class="mt-5" style="font-family: 'Poppins;">
            {{ user.name }}
          </h3>
          <h4 class="font-weight-regular">BSCS</h4>
          <div class="mt-3">
            <v-btn class="mx-2" icon="mdi-account-multiple-plus"></v-btn>
            <v-btn class="mx-2" icon="mdi-account-multiple-check"></v-btn>
            <v-btn class="mx-2" icon="mdi-account-eye"></v-btn>
            <v-btn class="mt-4" color="#1F6E8C" block>View Profile</v-btn>
          </div>
        </v-card>
      </v-navigation-drawer>
      <v-main>
        <div class="px-5">
          <v-card
            class="rounded-lg d-flex pa-5 align-center border-t-lg"
            style="border-color: #1f6e8c !important"
          >
            <v-avatar size="60" class="border">
              <v-img
                src="https://as2.ftcdn.net/v2/jpg/02/44/42/79/1000_F_244427911_aoHHulebtYy4wLpncBBuWqCTNFKolcCB.jpg"
              ></v-img>
            </v-avatar>
            <v-spacer></v-spacer>
            <v-btn color="#1F6E8C" flat class="text-capitalize"
              >Share your experience</v-btn
            >
          </v-card>
        </div>
      </v-main>
      <v-navigation-drawer
        location="right"
        flat
        floating
        class="border-0"
        color="transparent"
      >
        <v-card class="rounded-lg d-flex pa-5 flex-column">
          <div class="d-flex">
            <v-avatar size="60" class="border mr-2">
              <v-img
                src="https://as2.ftcdn.net/v2/jpg/02/44/42/79/1000_F_244427911_aoHHulebtYy4wLpncBBuWqCTNFKolcCB.jpg"
              ></v-img>
            </v-avatar>
            <div>
              <h3>Joshua Sotto</h3>
              <h5 class="font-weight-regular">25 minutes ago</h5>
            </div>
          </div>
          <div class="d-flex mt-2">
            <v-btn color="#1F6E8C" flat size="small" class="text-capitalize w-50"
              >Accept</v-btn
            >
            <v-btn color="transparent" flat size="small" class="text-capitalize w-50 ml-2"
              >Remove</v-btn
            >
          </div>
        </v-card>

        <div class="mt-4">
          <p>People connected with you</p>
        </div>
      </v-navigation-drawer>
    </v-layout>
  </AuthenticatedLayout>
</template>
