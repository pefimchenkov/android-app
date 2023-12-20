<template>
  <Page actionBarHidden="true" backgroundColor="#dfdfd5">
    <StackLayout height="60" verticalAlignment="top">
        <Button text="Get Users" @tap="getUsers" backgroundColor="rgb(12, 129, 80)" android:marginTop="20" />
    </StackLayout>
  </Page>
</template>

<script>

export default {
  data() {
    return {
        users: []
      }
    },

    methods: {
      getUsers() {
      fetch('https://jsonplaceholder.typicode.com/users')
        .then(response => response.json())
        .then(json => {
          this.users = json
          console.log(this.users)
        })
    },  
    }
  }

</script>

<style scoped lang="scss">
@import '@nativescript/theme/scss/variables/blue';
</style>
