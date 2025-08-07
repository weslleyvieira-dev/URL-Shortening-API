<script setup>
import { ref, watch } from "vue";

const isSubmitted = ref(false);
const isLoading = ref(false);
const url = ref("");
const copiedLink = ref("");
const error = ref("");
const duplicate = ref();
const links = ref([]);

async function shortUrl(inputUrl) {
  if (isLoading.value) return;
  isLoading.value = true;
  isSubmitted.value = true;

  if (!inputUrl) {
    error.value = "Please add a link";
    return;
  }

  duplicate.value = links.value.find(
    (element) => element.longLink === inputUrl
  );

  if (duplicate.value) {
    error.value = "This link is already shorted: ";
    return;
  }

  try {
    error.value = "";

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
      throw new Error(`Error status: ${response.status}`);
    }

    const data = await response.json();
    const newUrl = data.result_url;

    links.value.unshift({
      longLink: inputUrl,
      shortLink: newUrl,
    });
  } catch (e) {
    error.value = "Insert a valid URL";
    console.error(e);
  }
}

function copyLink(url) {
  navigator.clipboard.writeText(url);
  copiedLink.value = url;
}

watch(url, (newValue) => {
  const cleanUrl = newValue.replace(/\s/g, "");
  if (cleanUrl !== newValue) {
    url.value = cleanUrl;
  }

  error.value = "";
  isSubmitted.value = false;
  isLoading.value = false;
});
</script>

<template>
  <div class="shorter">
    <div class="shorter-input" :class="{ error: error }">
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
        <span v-if="isSubmitted && error" class="url-error">
          {{ error }}
          <a
            class="duplicated-link"
            v-if="duplicate"
            :href="duplicate.shortLink"
            target="_blank"
            >{{ duplicate.shortLink }}</a
          >
        </span>
      </div>
      <button
        :disabled="isLoading"
        v-on:click="shortUrl(url)"
        type="submit"
        class="submit"
      >
        Shorten It!
      </button>
    </div>
    <div class="links-container">
      <div class="item-container" v-for="item in links">
        <a :href="item.longLink" target="_blank" class="long-link">{{
          item.longLink
        }}</a>
        <div class="short-container">
          <a :href="item.shortLink" target="_blank" class="short-link">{{
            item.shortLink
          }}</a>
          <button
            v-on:click="copyLink(item.shortLink)"
            class="copy-btn"
            :class="{ copied: copiedLink === item.shortLink }"
          >
            {{ copiedLink === item.shortLink ? "Copied!" : "Copy" }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.shorter {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  background-color: var(--light-gray);
}

.shorter-input {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1.5rem;
  height: 10.5rem;
  margin: 0 10.313rem;
  border-radius: 0.625rem;
  transform: translateY(-5.25rem);
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

input.error {
  border: 3px solid var(--red);
}

.url-error {
  display: flex;
  gap: 0.5rem;
  color: var(--red);
  font-style: italic;
  position: absolute;
  bottom: -1.5rem;
  line-height: 1.125rem;
  letter-spacing: 0.11px;
}

.duplicated-link {
  color: var(--light-green);
  text-decoration: none;
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

.submit:disabled {
  cursor: not-allowed;
  background-color: var(--red);
}

.links-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 1.5rem;
  margin: 0 10.313rem;
  border-radius: 0.625rem;
  transform: translateY(-5.25rem);
}

.item-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 4.5rem;
  width: 100%;
  border-radius: 5px;
  padding: 0 1.5rem;
  box-sizing: border-box;
  background-color: white;
}

.short-container {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

.long-link,
.short-link {
  font-size: 1.25rem;
  letter-spacing: 0.15px;
  text-decoration: none;
}

.long-link {
  color: var(--dark-gray);
}

.short-link {
  color: var(--light-green);
}

.copy-btn {
  height: 2.5rem;
  width: 6.375rem;
  border-radius: 5px;
  border: none;
  color: white;
  cursor: pointer;
  background-color: var(--light-green);
}

.copy-btn:focus {
  background-color: var(--dark-purple);
}

.copied {
  background-color: var(--dark-purple);
}
@media (max-width: 1024px) {
  .shorter {
    transform: translateY(5rem);
  }

  .shorter-input {
    flex-direction: column;
    gap: 1rem;
    height: 10rem;
    margin: 0 1.5rem;
    background: var(--dark-purple)
      url("/assets/backgrounds/bg-shorten-mobile.svg") repeat center;
  }

  .shorter-input.error {
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
