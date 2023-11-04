<script setup>
import { usePage, router } from "@inertiajs/vue3";
import { computed } from "vue";
const $page = usePage();
const user = computed(() => $page.props.auth.user);
const logo = computed(() => $page.props.logo);
</script>

<template>
  <v-app>
    <v-app-bar flat color="#1f6e8c">
      <v-container class="d-flex align-center">
        <h3>
          <span
            style="background-color: white; color: #1f6e8c !important"
            class="pa-2 text-white rounded-lg mr-2"
            >Alumni</span
          >
          <span style="color: white">Tracking</span>
        </h3>
        <div class="w-33">
          <v-text-field
            hide-details
            variant="solo"
            density="compact"
            flat
            label="Search"
            single-line
            prepend-inner-icon="mdi-magnify"
            class="ml-5"
          ></v-text-field>
        </div>
        <v-spacer></v-spacer>
        <v-btn class="mr-2" icon="mdi-bell"></v-btn>
        <v-btn class="mr-4" icon="mdi-message-text"></v-btn>
        <v-menu location="bottom end">
          <template #activator="{ props }">
            <v-avatar v-bind="props">
              <v-img
                src="https://as2.ftcdn.net/v2/jpg/02/44/42/79/1000_F_244427911_aoHHulebtYy4wLpncBBuWqCTNFKolcCB.jpg"
              ></v-img>
            </v-avatar>
          </template>
          <v-card class="rounded-lg" width="250">
            <v-list>
              <v-list-item @click="router.post('/logout')" prepend-icon="mdi-logout"
                >Logout</v-list-item
              >
            </v-list>
          </v-card>
        </v-menu>
      </v-container>
    </v-app-bar>
    <v-app-bar density="compact" height="60" class="px-15">
      <v-container class="d-flex align-center px-15">
        <v-tabs grow class="px-15">
          <v-tab class="text-capitalize" size="small" prepend-icon="mdi-home">Home</v-tab>
          <v-tab class="text-capitalize" size="small" prepend-icon="mdi-calendar"
            >Latest Events</v-tab
          >
          <v-tab class="text-capitalize" size="small" prepend-icon="mdi-briefcase"
            >Job Opportunity</v-tab
          >
          <v-tab class="text-capitalize" size="small" prepend-icon="mdi-account-group"
            >batch mate</v-tab
          >
        </v-tabs>
      </v-container>
    </v-app-bar>
    <v-main class="bg-grey-lighten-4" style="padding-inline: 175px; padding-top: 130px">
      <slot></slot>
    </v-main>
  </v-app>
</template>
