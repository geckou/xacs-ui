<template>
  <div :class="$style.container">
    <SideNav
      :displayState="navDisplayState"
      @openNav="navDisplayState = true"
    >
      <!-- <div :class="$style.tabs">
        <NavContentSelectTab
          :selectedTab="selectedTab"
          @selected="tabSelected"
        />
      </div>
      <div>
        <NavTreeList
          v-show="selectedTab === 'tree'"
          :tagData="tagData"
        />
      </div> -->
    </SideNav>
    <div :class="$style.column">
      <GlobalHeader>
        <IconButton
          @onClick="navDisplayState = !navDisplayState"
        >
          <i class="bi bi-filter-left" />
        </IconButton>
      </GlobalHeader>
      <div :class="$style.contents">
        <slot />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
definePageMeta({
  name: 'DefaultLayout',
})

const navDisplayState = ref(true)
</script>

<style lang="scss" module>
@import url('https://fonts.googleapis.com/css2?family=M+PLUS+1p:wght@300;500&display=swap');

:root {
  --bv              : .5rem;
  --white-color     : #fff;
  --main-color      : #005AAF;
  --base-color      : #EEF1F2;
  --text-color      : #262A2C;
  --link-color      : #005AAF;
  --shadow-color    : rgba(20, 21, 21, .1);
  --line-height     : 1.4;
  --letter-spacing  : .01em;
  --base-font-size  : 14px;
  --large-font-size : 16px;
  --larger-font-size: 18px;
  --small-font-size : 12px;
  --min-font-size   : 10px;
}

html {
  scroll-behavior: smooth;
}

body {
  background-color     : var(--base-color);
  color                : var(--text-color);
  font-family          : 'M PLUS 1p', sans-serif;
  font-size            : var(--base-font-size);
  line-height          : var(--line-height);
  letter-spacing       : var(--letter-spacing);
  word-wrap            : break-word;
  font-feature-settings: 'palt';
}

main {
  flex: 1 1 auto;
}

p {
  margin : 0;
  padding: 0;
}

small,
span {
  display: inline-block;
}

h1, h2, h3, h4, h5, h6 {
  margin     : 0;
  padding    : 0;
  color      : inherit;
  font-weight: bold;
  font-size  : inherit;
  line-height: var(--line-height);
}

ul, ol, li, dl, dt, dd {
  margin : 0;
  padding: 0;
}

li {
  list-style: none;
}

a {
  color     : var(--link-color);
  transition: color .2s;
}

em {
  font-style: normal;
}

img {
  display   : block;
  max-width : 100%;
  max-height: 100%;
}

fieldset {
  border: none;
}

input,
option,
button {
  line-height   : 1.2;
  letter-spacing: var(--letter-spacing);
}

table {
  border-collapse: collapse;
  border-spacing: 0;

  th,
  td {
    text-align    : left;
    vertical-align: middle;
  }
}

.container {
  width  : 100vw;
  display: flex;

  .column {
    display       : flex;
    flex-direction: column;

    .contents {
      flex: 1 0 auto;
    }
  }
}
</style>