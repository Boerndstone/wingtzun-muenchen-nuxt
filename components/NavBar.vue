<template>
  <div class="navbar navbar-inverse" role="navigation">
    <div class="container">
      <div class="col-md-4 col-sm-6 col-xs-9">
        <a class="brand" href="/home">
          <img src="~/assets/images/wingtzun.svg" alt="Wing Tsun Kampfkunstschule" />
        </a>
      </div>
      <div class="navbar-header">
         <button
              type="button"
              class="navbar-toggle collapsed"
              @click="toggleNavbar"
            >
              <span class="sr-only">Toggle navigation</span>
              <span class="icon-bar"></span>
              <span class="icon-bar"></span>
              <span class="icon-bar"></span>
        </button>
      </div>
    </div>
    <div 
      id="navbar" 
      class="collapse navbar-collapse" 
      :class="{ 'in': isNavbarOpen }"
    >
      <div class="container">
        <ul class="nav navbar-nav">
          <li
            v-for="link in links"
            :key="link.id"
          >
            <nuxt-link
              :to="'/' + link.href"
              :exact="true"
              @click="closeNavbar"
            >{{ link.name }}</nuxt-link>
          </li>
          <li class="probe">
            <a href="/kontakt" @click="closeNavbar">Kostenloses Probetraining</a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      isNavbarOpen: false,
      links: [
        {
          id: 1,
          href: "home",
          name: "Home",
        },
        {
          id: 2,
          href: "wingtzun",
          name: "Wing Tzun",
        },
        {
          id: 3,
          href: "training",
          name: "Angebot",
        },
        {
          id: 4,
          href: "preise",
          name: "Preise",
        },
        {
          id: 5,
          href: "schule",
          name: "Das Team",
        },
        {
          id: 6,
          href: "termine",
          name: "News",
        },
        {
          id: 7,
          href: "kontakt",
          name: "Kontakt",
        },
      ],
    };
  },
  watch: {
    '$route'() {
      this.isNavbarOpen = false;
    }
  },
  methods: {
    toggleNavbar() {
      this.isNavbarOpen = !this.isNavbarOpen;
    },
    closeNavbar(route) {
      this.isNavbarOpen = false;
      this.$router.push(route);
    }
  }
};
</script>

<style scoped>
  .navbar-inverse .navbar-nav>li>a:hover, .navbar-inverse .navbar-nav>li>a:focus {
    background-color: red;
  }
</style>