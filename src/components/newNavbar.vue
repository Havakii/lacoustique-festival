<template>
    <v-layout>

        <v-app-bar>
            <v-navigation-drawer v-model="sidebar" app>
                <v-list>
                    <v-list-tile v-for="(item, index) in menuItems" :key="index">
                        <v-list-tile-content @click="handleNavClick(item.path)">
                            <v-btn @click="handleNavClick(item.path)">

                                {{ item.title }}
                            </v-btn>
                        </v-list-tile-content>
                    </v-list-tile>
                </v-list>
            </v-navigation-drawer>
    
            <v-toolbar app>
                <span class="hidden-sm-and-up">
                    <v-toolbar-side-icon @click="sidebar = !sidebar">
                    </v-toolbar-side-icon>
                </span>
                <v-toolbar-title>
                    <router-link to="/" tag="span" style="cursor: pointer">
                        {{ appTitle }}
                    </router-link>
                </v-toolbar-title>
                <v-spacer></v-spacer>
                <v-toolbar-items class="hidden-xs-only">
                    <v-btn flat v-for="(item, index) in menuItems" :key="index"
                        @click="handleNavClick(item.path)">
                        {{ item.title }}
                    </v-btn>
                </v-toolbar-items>
            </v-toolbar>
    
        </v-app-bar>
    </v-layout>

</template>

<script>

export default {
    data() {
        return {
            appTitle: 'Lacoustique',
            sidebar: false,
            menuItems: [
                { title: 'Accueil', path: 'Home'},
                { title: 'Programme', path: 'program'},
                { title: 'A propos', path: 'About' },
                { title: 'Infos pratiques', path: 'Information'}
            ]
        }
    },
    methods: {
        handleNavClick(path) {
            this.$emit('navigate', path)
        }
    }
};
</script>