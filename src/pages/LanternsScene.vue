<template>
  <Logo/>
  <GoToLink text="Homepage" link="#/" />
  <ARScenePage>
  <template #scene>
    <ARScene ref="ar-scene" :mindarImage="mindarImage" :modelsInTargets="modelsInTargets" :assets="assets"/>
    <ARScene ref="ar-scene" :mindarImage="mindarImage1" :modelsInTargets="modelsInTargets" :assets="assets"/>
  </template>
</ARScenePage>

</template>

<script>
import ARScenePage from './ARScenePage.vue'
import ARScene from "../components/ARScene.vue";
import {AAssetItem, AGltfModelData} from "../assets/aframe-helper.js";
import GoToLink from "./GoToLink.vue";
import Logo from "../components/Logo.vue"

export default {
  name: "LanternsScene",
  components: {
    ARScenePage,
    ARScene,
    GoToLink,
    Logo,
  },
  data(){
    const commonScale = 1.5;
    const commonPositionY = -0.5;
    return {
      mindarImage1:{
        targetSrc: "./targets/maskTarget.mind",
        filterMinCF: 0.00001,
        filterBeta: 0.001
      },
      mindarImage:{
        targetSrc: "./targets/targets-final.mind",
        filterMinCF: 0.00001,
        filterBeta: 0.001
      },
      assets:[
        new AAssetItem("lantern-1-glb", "./3d-models/Mask6.glb"),
        new AAssetItem("lantern-1-glb", "./3d-models/Mask6.glb"),
      ],
      modelsInTargets:[
        [
          new AGltfModelData("lantern-1", "#lantern-1-glb",{
            positionX:-.25,
            scale: 0.5,
            positionY:0.5,
            animationClip: "Breath",
            rotationX: 0,
            positionZ: -1
          }),
          new AGltfModelData("lantern-1", "#lantern-1-glb",{
            positionX:-.25,
            scale: 0.5,
            positionY:0.5,
            animationClip: "Breath",
            rotationX: 0,
            positionZ: -1
          }),
        ],
        // [
        //   new AGltfModelData("lantern-2", "#lantern-2-glb",{
        //     scale: 1.2,
        //     positionY:commonPositionY,
        //   }),
        // ],
        // [
        //   new AGltfModelData("lantern-3", "#lantern-3-glb",{
        //     positionX:2.75,
        //     positionY:commonPositionY,
        //     scale: commonScale
        //   }),
        // ]
      ],

    }
  }
}
</script>

<style scoped>
/*pass this to inner component*/
/* :deep(#mihintale-button-text) {
  margin-top: 0 !important;
} */
:deep(.selection-button){

}
</style>