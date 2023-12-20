<template>
  <Page class="page">
    <ActionBar class="action-bar">
      <NavigationButton visibility="hidden" />
      <GridLayout columns="50, *">
        <Label class="action-bar-title" text="Главная" colSpan="2" />

        <Label class="fas" text.decode="&#xf0c9;" @tap="onDrawerButtonTap" />
      </GridLayout>
    </ActionBar>

    <StackLayout>
      <Label class="page__content-icon fas" text.decode="&#xf015;" />
      <Label v-if="date" class="page__content-placeholder label" :text="message" />
      <Label v-if="date" class="page__content-placeholder label" :text="date" />

      <DatePicker class="page__content" v-model="date" backgroundColor="#fff" @dateChange="onPickDateTap" />

    </StackLayout>



  </Page>
</template>

<script>
import * as utils from "~/shared/utils";
import { SelectedPageService } from "../shared/selected-page-service";

export default {
  data() {
    return {
      date: null,
    }
  },
  mounted() {
    SelectedPageService.getInstance().updateSelectedPage("Home");
  },
  computed: {
    message() {
      return "Привет, вы на главной странице!";
    }
  },
  methods: {

    onDrawerButtonTap() {
      utils.showDrawer();
    },

    onPickDateTap: function (args) {
      console.log(this.date)
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
