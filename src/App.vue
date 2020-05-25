<template>
    <div id="app">
        <div class="section container">
            <div class="columns is-mobile">
                <div class="column is-2">
                    <a href="https://www.khabubundivhu.co.za" target="_blank">
                        <h1 v-if="darkMode ===true"  class="white-logo">Khabubu Ndivhu</h1>
                        <h1 v-else class="black-logo">Khabubu Ndivhu</h1>
                    </a>
                </div>
                <div class="column is-9">
                </div>
                <div class="column is-1">
                    <input type="checkbox" id='theme-switch' class='theme-switch' v-model="darkMode"/>
                    <label for='theme-switch'>
                        <span v-if="darkMode === true">
                            <img alt="logo" src="./assets/images/sun.png" width="40">
                        </span>
                        <span v-else>
                            <img alt="logo" src="./assets/images/moon.png" width="40">
                        </span>
                    </label>
                </div>
            </div>

            <section class="hero is-medium has-text-centered">
                <div class="hero-body">
                    <div class="container">
                        <h1 class="title dynamic-title">
                            <span v-if="darkMode === true">Dark Theme</span>
                            <span v-else>Light Theme</span>
                        </h1>
                        <h2 class="subtitle dynamic-subtitle">Create Multiple Themes in Vue.js</h2>
                    </div>
                </div>
            </section>

        </div>

    </div>
</template>

<script>
    export default {
        name: 'app',
        data() {
            return {
                darkMode: false,
            }
        },
        mounted() {
            // set page title
            document.title = 'Multiple Themes in Vue.js';
            // set 'app-background' class to body tag
            let bodyElement = document.body;
            bodyElement.classList.add("app-background");
            // check for active theme
            let htmlElement = document.documentElement;
            let theme = localStorage.getItem("theme");
            if (theme === 'dark') {
                htmlElement.setAttribute('theme', 'dark')
                this.darkMode = true
            } else {
                htmlElement.setAttribute('theme', 'light');
                this.darkMode = false
            }
        },
        watch: {
            darkMode: function () {
                // add/remove class to/from html tag
                let htmlElement = document.documentElement;
                if (this.darkMode) {
                    localStorage.setItem("theme", 'dark');
                    htmlElement.setAttribute('theme', 'dark');
                } else {
                    localStorage.setItem("theme", 'light');
                    htmlElement.setAttribute('theme', 'light');
                }
            }
        }
    }
</script>

<style scoped>
 .white-logo {
   color: white;
   font-weight: bold;
 }
 .black-logo {
   color: black;
   font-weight: bold;
 }
</style>