<script setup>
import { ref } from "vue";

const url = ref("");
const isSubmitted = ref(false);
const error = ref("");
const shortLink = ref("");

async function shortUrl(inputUrl) {
  if (!inputUrl) {
    error.value = "Please add a link";
    shortLink.value = "";
    isSubmitted.value = true;
    return;
  }

  try {
    isSubmitted.value = true;
    error.value = "";
    shortLink.value = "";

    const response = await fetch(
      "https://corsproxy.io/?https://cleanuri.com/api/v1/shorten",
      {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          url: inputUrl,
        }),
      }
    );

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    const data = await response.json();
    console.log("URL encurtada:", data.result_url);
    shortLink.value = data.result_url;
  } catch (e) {
    error.value = "Insert a valid URL";
    console.error(e);
  }
}
</script>

<template>
  <div class="shorter" :class="{ error: error }">
    <div class="url-container">
      <input
        id="url"
        v-model.trim="url"
        type="url"
        placeholder="Shorten a link here..."
        class="url-input"
        :class="{ error: error }"
        @keydown.enter="shortUrl(url)"
      />
      <span v-if="isSubmitted && error" class="url-error">{{ error }}</span>
    </div>
    <button v-on:click="shortUrl(url)" type="submit" class="submit">
      Shorten It!
    </button>
  </div>
</template>

<style scoped>
.shorter {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1.5rem;
  height: 10.5rem;
  margin: 0 10.313rem;
  border-radius: 0.625rem;
  background: var(--dark-purple)
    url("/assets/backgrounds/bg-shorten-desktop.svg") repeat-x center;
}

.url-container {
  display: flex;
  position: relative;
}

.url-input {
  width: 48.125rem;
  height: 4rem;
  border: none;
  border-radius: 0.625rem;
  padding: 0 2rem;
  box-sizing: border-box;
  font-size: 1.25rem;
  letter-spacing: 0.15px;
}

.url-input::placeholder {
  color: var(--dark-gray);
  opacity: 0.5;
}

.error {
  border: 3px solid var(--red);
}

.url-error {
  color: var(--red);
  font-style: italic;
  position: absolute;
  bottom: -1.5rem;
  line-height: 1.125rem;
  letter-spacing: 0.11px;
}

.submit {
  width: 11.75rem;
  height: 4rem;
  border: none;
  border-radius: 0.625rem;
  font-family: "Poppins-SemiBold";
  font-size: 1.25rem;
  background-color: var(--light-green);
  color: white;
}

.submit:hover {
  background-color: var(--lighter-green);
}

@media (max-width: 1024px) {
  .shorter {
    flex-direction: column;
    gap: 1rem;
    height: 10rem;
    margin: 0 1.5rem;
    background: var(--dark-purple)
      url("/assets/backgrounds/bg-shorten-mobile.svg") repeat center;
  }

  .shorter.error {
    height: 11.375rem;
  }

  .url-container {
    flex-direction: column;
    gap: 0.25rem;
  }

  .url-input {
    width: 17.5rem;
    height: 3rem;
    padding: 0 1rem;
    font-size: 1rem;
    letter-spacing: 0.12px;
  }

  .url-error {
    position: static;
    line-height: 1.125rem;
    letter-spacing: 0.11px;
  }

  .submit {
    width: 17.5rem;
    height: 3rem;
    font-size: 1.125rem;
  }
}
</style>
