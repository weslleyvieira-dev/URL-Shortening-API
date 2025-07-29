<script setup>
import Header from "./components/Header.vue";
</script>

<template>
  <Header />

  <main>
    <div class="hero">
      <div class="hero-info">
        <h1>More than just shorter links</h1>
        <p>
          Build your brand's recognition and get detailed insights on how your
          links are performing.
        </p>
        <button>Get Started</button>
      </div>
      <img
        class="hero-img"
        src="/assets/images/illustration-working.svg"
        alt="Ilustração"
      />
    </div>
  </main>

  <footer></footer>
</template>

<style scoped>
main {
  overflow-x: hidden;
}

.hero {
  display: flex;
  align-items: center;
  margin: 4.875rem 0 4.875rem 10.375rem;
  height: 30.125rem;
}

.hero-info {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 21.938rem;
  width: 36.25rem;
  position: relative;
}

.hero-info h1 {
  font-family: "Poppins-SemiBold";
  font-size: 5rem;
  color: var(--dark-gray);
  line-height: 5.625rem;
  letter-spacing: -2px;
}

.hero-info p {
  font-size: 1.375rem;
  color: var(--gray);
  line-height: 2.25rem;
  letter-spacing: 0.15px;
  margin: 0.375rem 0 2.375rem;
}

.hero-info button {
  width: 12.313rem;
  height: 3.5rem;
  border: none;
  border-radius: 1.75rem;
  font-family: "Poppins-Bold";
  font-size: 1.25rem;
  color: white;
  background-color: var(--light-green);
}

.hero-info button:hover {
  cursor: pointer;
  background-color: var(--lighter-green);
}

.hero-img {
  z-index: -1;
  position: absolute;
  right: -6.44rem;
}

@media (max-width: 1024px) {
  .hero {
    flex-direction: column-reverse;
    height: 41.438rem;
    margin: 1.5rem;
    gap: 2.25rem;
  }

  .hero-img {
    width: 511px;
    height: 337px;
    position: relative;
    right: 0;
    transform: translateX(5.75rem);
  }

  .hero-info {
    align-items: center;
    height: 18.063rem;
    width: 100%;
  }

  .hero-info h1 {
    font-size: 2.625rem;
    line-height: 3rem;
    letter-spacing: -1.05px;
    text-align: center;
  }

  .hero-info p {
    font-size: 1.125rem;
    color: var(--gray);
    line-height: 1.875rem;
    letter-spacing: 0.12px;
    text-align: center;
    margin: 0.938rem 0 2rem;
  }

  .hero-info button {
    width: 12.313rem;
    height: 3.5rem;
    border: none;
    border-radius: 1.75rem;
    font-family: "Poppins-Bold";
    font-size: 1.25rem;
    color: white;
    background-color: var(--light-green);
  }

  .hero-info button:hover {
    cursor: pointer;
    background-color: var(--lighter-green);
  }
}
</style>
