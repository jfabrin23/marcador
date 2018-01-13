<template>
  <div>
    <div class="header wrap container align-center">
      <div class="logo flex clicavel" @click="$router.push('home')">
      </div>
    </div>
  </div>
</template>
<script>
export default {
  computed: {
    user () {
      return this.$store.state.user
    }
  },
  data () {
    return {
      inAtivar: false,
      inUser: false
    }
  },
  methods: {
    bodyDrawer (option) {
      switch (option) {
        case 'user':
          this.inUser = true
          break
      }
    }
  }
}
</script>

<style lang="css" scoped>
  .header {
    z-index: 9997;
    background-image: url('../assets/banner.png');
    background-size: cover;
    width: 100vw;
    height: 20vh;
    background-color: var(--corVerdeLink);
    align-items: center;
  }

  .header .logo img{
    height: 5vh;
    padding: 1vh
  }

  .header h1{
    color: var(--corSecundaria);
    padding-left: 1vw;
  }

  .header .link{
    padding-left: 1vw;
    padding-right: 1vw;
    color: var(--corSecundaria);
    cursor: pointer;
  }

  .header .link:hover{
    color: var(--corTextoHover)
  }
</style>
