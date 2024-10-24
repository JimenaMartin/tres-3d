<script setup lang="ts">
import { watch } from 'vue';
import { useGLTF, Levioso, Html } from '@tresjs/cientos';
import { useState } from '../composables/state';

const { nodes, materials } = await useGLTF('/models/headphones/headphones.gltf');

const model = nodes['Headphones_7'];

const { selectedBaseColor, selectedCushionColor } = useState()

watch(selectedBaseColor, (color) => {
    materials.Base.color.set(color);
});

watch(selectedCushionColor, (color) => {
    materials.Cush.color.set(color);
});

</script>

<template>
    <Levioso>
        <primitive :object="model" />
    </Levioso>
</template>