<template>
  <Page class="page">
    <ActionBar class="action-bar">
      <NavigationButton visibility="hidden" />
      <GridLayout columns="50, *">
        <Label class="action-bar-title" text="Users" colSpan="2" />

        <Label class="fas" text.decode="&#xf0c9;" @tap="onDrawerButtonTap" />
      </GridLayout>
    </ActionBar>


    <StackLayout>
      <Label class="page__content-icon fas" text.decode="&#xf0c0;" />
      <Button  text="Get Users" @tap="getUsers" backgroundColor="rgb(12, 129, 80)" />
       <Label v-if="loading" class="page__content-placeholder label" text="Загружаем..." />

      <ListView
        for="user in users"
        @itemTap="onItemTap"
      >
        <v-template>
          <Label :text="user.name" />
        </v-template>
      </ListView>


    </StackLayout>
  </Page>
</template>

<script>
import * as utils from "~/shared/utils";
import { SelectedPageService } from "../shared/selected-page-service";
import { Screen } from '@nativescript/core';

import UserDetails from './UserDetails'

export default {
  components: {
    UserDetails,
  },


  data() {
    return {
      users: [],
      loading: false
    }
  },

  mounted() {
    SelectedPageService.getInstance().updateSelectedPage("Users");
  },

  computed: {
    message() {
      return "<!-- Page content goes here -->";
    }
  },

  methods: {
    onDrawerButtonTap() {
      utils.showDrawer();
    },

    getUsers() {
      this.loading = true
      fetch('https://jsonplaceholder.typicode.com/users')
        .then(response => response.json())
        .then(json => {
          setTimeout(() => {
            this.users = json
            this.loading = false
          }, 2000)
        })
    },

    onItemTap(val) {
      this.$navigateTo(UserDetails, {
        transition: {
          name: "slideLeft",
          duration: 300,
          curve: "easeIn"
        },
        props: val.item
      })

      console.log(Screen.mainScreen.heightDIPs)
    },

  }
};
</script>

<style scoped lang="scss">
// Start custom common variables
@import '@nativescript/theme/scss/variables/blue';
// End custom common variables

// Custom styles
</style>
