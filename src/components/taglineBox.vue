<template>
  <div
    class="absolute top-[-50px] z-10 flex w-full items-center justify-center transition-all"
    :class="
      scrollPost >= 100 ? 'opacity-1 translate-y-0' : 'translate-y-10 opacity-0'
    "
  >
    <div class="max-w-[1000px]">
      <div class="flex flex-col gap-5 bg-primary p-6 text-white shadow-lg">
        <h1 class="rounded-md text-center text-[1.7vw] font-semibold italic">
          Nurturing Tomorrow's Leaders with Love and Learning
        </h1>
        <!-- <div class="text-center">
               <a
                  href=""
                  class="rounded-sm bg-green-500 px-3 py-2 text-lg font-bold"
                  >Inquire Us</a
               >
            </div> -->
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import { translate } from "element-plus";

export default {
  setup() {
    const scrollPost = ref();
    return { scrollPost };
  },
  methods: {
    scroll() {
      this.scrollPost = window.scrollY || window.pageYOffset;
    },
  },
  mounted() {
    window.addEventListener("scroll", this.scroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.scroll);
  },
};
</script>

<style lang="scss" scoped></style>
