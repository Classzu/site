<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" />
        <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />

        {{ hey }}
        {{ heyStore }}
        <button @click="getHey()">getHey</button>
        <input type="text" v-model="form" />
        <button @click="onSubmit">update</button>

        <div id="myDiv" style="height: 500px; border: 1px solid"></div>
    </div>
</template>

<script lang="ts">
import { computed, defineComponent, ref, reactive, onMounted } from 'vue';
import { useStore } from '@/store/index';
import HelloWorld from '@/components/HelloWorld.vue';
import MutationTypes from '@/store/mutationTypes';

import Classzu from 'classzu';

export default defineComponent({
    name: 'Home',
    components: {
        HelloWorld,
    },
    setup() {
        onMounted(() => {
            const classzu = new Classzu();
            classzu.setup('myDiv');
        });

        const form = ref('');

        const clearForm = () => {
            form.value = '';
        };

        const hey = ref('HEYYYYYYYYY');

        function getHey() {
            console.log('hEYYYYYYY?????');
        }

        // store
        const store = useStore();
        const heyStore = computed(() => store.state.heyStore);
        console.log(heyStore);

        const onSubmit = () => {
            store.commit(MutationTypes.setHeyStore, form.value);
            clearForm();
        };

        return {
            form,
            hey,
            getHey,
            heyStore,
            onSubmit,
        };
    },
});
</script>
