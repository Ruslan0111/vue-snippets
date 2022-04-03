<template>
  <div>
    <div class="img">
      <transition name="fade">
        <p v-if="isLoading" class="loader">Loading...</p>
      </transition>

      <img
        @load="onLoad"
        src="https://images.unsplash.com/photo-1632351459705-22a52c7a3d1d?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8N3x8ZmV0Y2h8ZW58MHx8MHx8&auto=format&fit=crop&w=500&q=60"
        alt=""
      />
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  name: "TestView",

  setup() {
    const isLoading = ref(true);

    function onLoad(e) {
      console.log("load", e);
      isLoading.value = false;
    }

    return {
      isLoading,
      onLoad,
    };
  },
};
</script>

<style scoped>
.img {
  width: 500px;
  height: 600px;
  border: 2px solid red;
  position: relative;
}

.img img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.loader {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1;
  background-color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 22px;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}
</style>
