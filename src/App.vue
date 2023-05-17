<script setup>
import { useDark, useToggle } from '@vueuse/core'
import { watch } from 'vue'
const isDark = useDark()

const toggleDark = useToggle(isDark)

watch(isDark, value => {
    if (value) {
        window.less.modifyVars({
            '@primary-color': 'cyan',
        })
    } else {
        window.less.modifyVars({
            '@primary-color': 'pink',
        })
    }
})
</script>

<template>
    <main>
        <a-button type="primary">Primary Button</a-button>
        <button @click="toggleDark()">切换</button>
    </main>
</template>

<style scoped>
main {
    padding-top: 20px;
}

/* header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
