<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-light bg-light fixed-top">
      <!-- brand name in navbar -->
      <router-link class="navbar-brand" to="/">Bomb Shrimper 🍤</router-link>
      <!-- collapsed navbar button -->
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbar-collapse"
        aria-controls="navbar-collapse"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <!-- navbar -->
      <div class="collapse navbar-collapse" id="navbar-collapse">
        <ul class="navbar-nav ml-auto">
          <li class="nav-item">
            <router-link class="nav-link" to="/" active-class="active" exact>Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/search" active-class="active" exact>Search</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/about" active-class="active" exact>Get Started</router-link>
          </li>
          <!-- login navbar button, only shown when user is not logged in -->
          <li class="nav-item" v-if="!this.$store.getters.isLoggedIn">
            <router-link class="nav-link" to="/login" active-class="active" exact>Log in</router-link>
          </li>
          <!-- user account navbar button, only shown when user is logged in -->
          <li class="nav-item dropdown" v-if="this.$store.getters.isLoggedIn">
            <a class="nav-link dropdown-toggle" data-toggle="dropdown">
              <i class="fas fa-user mr-2"></i>
              Hi, {{ this.$store.getters.getUserName }}
            </a>
            <div class="dropdown-menu dropdown-menu-right">
              <span class="dropdown-item" @click="goToMyAccount">My Account</span>
              <span
                class="dropdown-item"
                @click="goToMyHouses"
                v-if="$store.getters.getUserRole === 'provider'"
              >My Houses</span>
              <span class="dropdown-item" @click="goToMySaveList">My Save List</span>
              <div class="dropdown-divider"></div>
              <span class="dropdown-item" @click="logout">Log out</span>
            </div>
          </li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<script>
import $ from "jquery";

export default {
  name: "Header",
  methods: {
    logout() {
      window.console.log(
        "getters.isLoggedIn: ",
        this.$store.getters.isLoggedIn
      );

      if (this.$store.getters.isLoggedIn) {
        this.$swal({
          title: "Confirm",
          text: "Are you sure you want to log out?",
          icon: "warning",
          buttons: true,
          dangerMode: true
        }).then(choice => {
          if (choice) {
            this.$axios
              .get("/api/users/logout/" + this.$store.getters.getUserId)
              .then(res => {
                if (res.status == 200) {
                  this.$store.commit("logout");
                  window.console.log("user logged out");

                  this.$swal("Success", "You are logged out!", "success").then(
                    () => {
                      window.location.reload(true);
                    }
                  );

                  if (this.$router.currentRoute.name !== "home") {
                    this.$router.push({ name: "home" });
                  }
                }
              })
              .catch(err => window.console.log(err));
          }
        });
      } else {
        window.console.log("You are not logged in!");
      }
    },
    goToMyAccount() {
      if (this.$router.currentRoute.name !== "myAccount") {
        this.$router.push({ name: "myAccount" });
      }
    },
    goToMyHouses() {
      if (this.$router.currentRoute.name !== "myHouses") {
        this.$router.push({ name: "myHouses" });
      }
    },
    goToMySaveList() {
      if (this.$router.currentRoute.name !== "mySaveList") {
        this.$router.push({ name: "mySaveList" });
      }
    }
  },
  watch: {
    $route() {
      $("#navbar-collapse").collapse("hide");
    }
  }
};
</script>


<style scoped>
.navbar-brand {
  font-size: 2rem;
}
.navbar {
  min-height: 100px;
}

.navbar-light .navbar-nav .nav-link.active {
  color: #3c9d9b;
}

.nav-item::after {
  content: "";
  display: block;
  width: 0px;
  height: 2px;
  background: #3c9d9b;
  transition: 0.2s;
}
.nav-item:hover::after {
  width: 100%;
}

.nav-link {
  padding: 15px 5px;
  transition: 0.2s;
}

.navbar-light .navbar-nav .nav-link.active {
  color: #3c9d9b;
}

.dropdown-menu {
  min-width: 0;
}
.dropdown-item {
  font-size: 14px;
  color: gray;
}

.dropdown-item:active {
  color: #212529;
}
.dropdown-item:focus,
.dropdown-item:hover {
  background: #3c9d9b;
}
</style> 