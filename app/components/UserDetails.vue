<template>
  <Page class="page">
    <ActionBar class="action-bar">
      <NavigationButton visibility="hidden" />
      <GridLayout columns="50, *">
        <Label class="fas" text.decode="&#xf04a;" @tap="$navigateBack" />
      </GridLayout>
    </ActionBar>

    <StackLayout class="page__content">
            <Label class="page__content-placeholder" :text="`ID: ` + id"/>
            <Label class="page__content-placeholder" :text="`Name: ` + name"/>
            <Label class="page__content-placeholder" :text="`Email: ` + email"/>
            <Label class="page__content-placeholder" :text="`Address: ` + address.city"/>
            <Label class="page__content-placeholder" :text="`Phone: ` + phone"/>
            <Label class="page__content-placeholder" :text="`Website: ` + website"/>
            <Label class="page__content-placeholder" :text="`Company: ` + company.name"/>
        </StackLayout>
    </Page>
</template>

<script>

export default {
  props: ['id', 'name', 'email', 'address', 'phone', 'website', 'company'],
  data() {
    return {
      details: [],
      message: "this is user details information..."
    }
  },

  methods: {
  }
};
</script>

<style scoped lang="scss">
@import '@nativescript/theme/scss/variables/blue';
</style>
