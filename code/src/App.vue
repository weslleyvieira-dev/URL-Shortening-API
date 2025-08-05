<script setup>
import Header from "./components/Header.vue";
import Shorter from "./components/Shorter.vue";
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

    <Shorter class="shorter" />

    <div class="about">
      <div class="about-title">
        <h1>Advanced Statistics</h1>
        <p>
          Track how your links are performing across the web with our advanced
          statistics dashboard.
        </p>
      </div>
      <div class="about-info">
        <div class="about-info-box">
          <div class="img">
            <img
              src="/assets/icons/icon-brand-recognition.svg"
              alt="Brand Recognition"
            />
          </div>
          <h2>Brand Recognition</h2>
          <p>
            Boost your brand recognition with each click. Generic links don't
            mean a thing. Branded links help instil confidence in your content.
          </p>
        </div>
        <div class="about-info-box">
          <div class="img">
            <img
              src="/assets/icons/icon-detailed-records.svg"
              alt="Detailed Records"
            />
          </div>
          <h2>Detailed Records</h2>
          <p>
            Gain insights into who is clicking your links. Knowing when and
            where people engage with your content helps inform better decisions.
          </p>
        </div>
        <div class="about-info-box">
          <div class="img">
            <img
              src="/assets/icons/icon-fully-customizable.svg"
              alt="Fully Customizable"
            />
          </div>
          <h2>Fully Customizable</h2>
          <p>
            Improve brand awareness and content discoverability through
            customizable links, supercharging audience engagement.
          </p>
        </div>
        <div class="line"></div>
      </div>
    </div>
  </main>

  <footer></footer>
</template>

<style scoped>
.hero {
  display: flex;
  align-items: center;
  margin: 4.875rem 0 0 10.375rem;
  height: 30.125rem;
  position: relative;
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

.shorter {
  transform: translateY(5.25rem);
}

.about {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 12.75rem 10.25rem 7.5rem;
  min-height: 36.5rem;
  gap: 6.25rem;
  background-color: var(--light-gray);
}

.about-title {
  display: flex;
  flex-direction: column;
  width: 33.75rem;
  gap: 1.125rem;
  text-align: center;
}

.about-title h1 {
  font-family: "Poppins-SemiBold";
  font-size: 2.5rem;
  line-height: 3rem;
  letter-spacing: -1px;
  color: var(--dark-gray);
}

.about-title p {
  font-size: 1.125rem;
  line-height: 2rem;
  letter-spacing: 0.12px;
  color: var(--gray);
}

.about-info {
  display: flex;
  gap: 1.875rem;
  position: relative;
}

.about-info .line {
  position: absolute;
  top: 50%;
  height: 0.5rem;
  width: 100%;
  transform: translateY(-50%);
  background-color: var(--light-green);
}

.about-info-box {
  display: flex;
  flex-direction: column;
  width: 21.875rem;
  height: 16.688rem;
  border-radius: 5px;
  padding: 0 2rem;
  box-sizing: border-box;
  background-color: white;
  z-index: 1;
  position: relative;
}

.about-info-box:nth-child(2) {
  margin-top: 2.75rem;
}

.about-info-box:nth-child(3) {
  margin-top: 5.5rem;
}

.about-info-box .img {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 5.5rem;
  height: 5.5rem;
  border-radius: 50%;
  transform: translateY(-50%);
  background-color: var(--dark-purple);
}

.about-info-box img {
  width: 2.5rem;
  height: 2.5rem;
}

.about-info-box h2 {
  font-family: "Poppins-SemiBold";
  font-size: 1.375rem;
  color: var(--dark-gray);
  margin-bottom: 0.75rem;
}

.about-info-box p {
  font-size: 0.938rem;
  line-height: 1.625rem;
  color: var(--gray);
}

@media (max-width: 1024px) {
  .hero {
    flex-direction: column-reverse;
    height: 41.438rem;
    margin: 1.5rem 1.5rem 5.5rem;
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

  .about {
    padding: 10rem 1.5rem 5rem;
    min-height: 77.625rem;
    gap: 5.75rem;
  }

  .about-title {
    width: 20.5rem;
    gap: 1rem;
  }

  .about-title h1 {
    font-size: 1.75rem;
    letter-spacing: -0.7px;
  }

  .about-title p {
    font-size: 1rem;
    line-height: 1.75rem;
    letter-spacing: 0.11px;
  }

  .about-info {
    flex-direction: column;
    gap: 5.75rem;
  }

  .about-info .line {
    height: 100%;
    width: 0.5rem;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
  }

  .about-info-box {
    align-items: center;
    text-align: center;
    width: 20.438rem;
  }

  .about-info-box:nth-child(2),
  .about-info-box:nth-child(3) {
    margin-top: 0;
  }
}
</style>
