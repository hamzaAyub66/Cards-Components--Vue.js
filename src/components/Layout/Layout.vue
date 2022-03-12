<template>
    <v-app class="pa-6">
        <Header />
        <v-main class="content">
            <router-view />
        </v-main>
    </v-app>
</template>

<script>
    import Header from '@/components/Header/Header';
    import './Layout.scss';

    export default {
        name: 'Layout',
        components: { Header,},
    };
</script>

<style src="./Layout.scss" lang="scss" />
