<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" />
        <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />

        {{ hey }}
        <button @click="getHey()"></button>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

export default defineComponent({
    name: 'Home',
    components: {
        HelloWorld,
    },
    setup() {
        const hey = ref('HEYYYYYYYYY');

        function getHey() {
            console.log('hEYYYYYYY?????');
        }

        return {
            hey,
            getHey,
        };
    },
});
</script>
