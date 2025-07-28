<script setup>
import { ref } from "vue";

const isMenuOpen = ref(false);

function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value;
}
</script>

<template>
  <header>
    <div class="pages">
      <img class="logo" src="/assets/images/logo.svg" alt="Shortly Logo" />
      <nav class="links" :class="{ show: isMenuOpen }">
        <p>Features</p>
        <p>Pricing</p>
        <p>Resources</p>
      </nav>
    </div>
    <div class="login" :class="{ show: isMenuOpen }">
      <div class="line" :class="{ show: isMenuOpen }"></div>
      <p>Login</p>
      <button>Sign Up</button>
    </div>
    <img
      class="menu"
      src="/assets/icons/icon-menu.svg"
      alt="Menu"
      @click="toggleMenu"
    />
  </header>
</template>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 2.5rem;
  margin: 3rem 10.375rem 0;
}

.pages {
  display: flex;
  align-items: center;
  gap: 2.813rem;
}

.links {
  display: flex;
  align-items: center;
  gap: 1.813rem;
}

p {
  font-family: "Poppins-Bold";
  color: var(--gray);
}

p:hover {
  cursor: pointer;
  color: var(--dark-gray);
}

.login {
  display: flex;
  align-items: center;
  gap: 2.25rem;
}

button {
  width: 6.5rem;
  height: 2.5rem;
  border: none;
  border-radius: 1.75rem;
  font-family: "Poppins-Bold";
  color: white;
  background-color: var(--light-green);
}

button:hover {
  cursor: pointer;
  background-color: var(--lighter-green);
}

.menu,
.line {
  display: none;
}

@media (max-width: 1023px) {
  header {
    height: 2rem;
    margin: 2.5rem 1.5rem 0;
  }

  .menu {
    display: block;
  }

  .links,
  .login {
    display: none;
    gap: 1.875rem;
  }

  .links.show,
  .login.show {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 6rem;
    right: 0;
    background-color: var(--dark-purple);
    width: -moz-available;
    width: -webkit-fill-available;
    margin: 0 1.5rem;
    padding: 2.5rem 1.5rem;
    border-radius: 0.625rem 0.625rem 0 0;
    height: fit-content;
    transform: translateX(0);
    z-index: 2;
  }

  .login.show {
    top: 18rem !important;
    padding-top: 1rem !important;
    border-radius: 0 0 0.625rem 0.625rem !important;
  }

  .line.show {
    display: unset;
    height: 1px;
    width: 17.5rem;
    background-color: var(--gray);
    opacity: 0.25;
  }

  p {
    font-size: 1.125rem;
    color: white;
  }

  button {
    width: 17.5rem;
    height: 3rem;
  }
}
</style>
