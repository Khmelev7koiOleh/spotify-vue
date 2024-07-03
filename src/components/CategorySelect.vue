<script setup>
import { ref, toRefs } from "vue";
import { RouterLink } from "vue-router";
import uniqolor from "uniqolor";

let randColor = ref("");
randColor.value = uniqolor.random("");

const props = defineProps({
  category: String,
  image: String,
});
const { category } = toRefs(props);
</script>
<template>
  <RouterLink>
    <div
      v-if="randColor"
      :style="`background-color:${randColor.color};`"
      class="conrtast-[2] brightness-[0.87] aspect-square rounded-xl relative overflow-hidden hover:opacity-[70%]"
    >
      <div class="text-white font-semibold pl-4 pt-3 text-[23px]">
        {{ category }}
      </div>
      <img
        class="absolute contrast-[0.55] -right-3.5 bottom-0 max-w-[100px] rotate-[20deg]"
        :src="image || ''"
        alt=""
      />
    </div>
  </RouterLink>
</template>
