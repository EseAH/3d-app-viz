<script setup lang="ts">
import { Stars, OrbitControls } from "@tresjs/cientos";
import { TresCanvas } from "@tresjs/core";
import { BasicShadowMap, SRGBColorSpace, NoToneMapping } from 'three';
import Houston from "./Model3d.vue";

const gl = {
    clearColor: '#181C3E',
    shadows: true,
    alpha: false,
    shadowMapType: BasicShadowMap,
    outputColorSpace: SRGBColorSpace,
    toneMapping: NoToneMapping,
}

</script>
<template>
    <div class="tres-container">
        <TresCanvas v-bind="gl">
            <TresPerspectiveCamera :position="[5, 5, 5]" :look-at="[0, 1, 0]" />
            <!-- <TresMesh>
                <TresSphereGeometry :args="[1, 32, 32]" />
                <TresMeshNormalMaterial />
            </TresMesh> -->
            <Stars />
            <OrbitControls />
            <Suspense>
                <Houston/>
            </Suspense>
            <TresAmbientLight :color="0xfffffff" :intensity="1"/>
            <TresDirectionalLight :position="[4, 6, 4]" :intensity="1" cast-shadow color="#fff" />
            <TresDirectionalLight :position="[4, 6, 4]" :intensity="2" cast-shadow color="white" />
        </TresCanvas>
    </div>
</template>

<style>
.tres-container {
    width: 100%;
    height: 400px;
}

canvas {
    width: 100%;
    height: 100%;
}
</style>