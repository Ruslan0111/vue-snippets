<template>
  <div class="about">
    <img v-if="image" :src="image" alt="" />
    <p v-else>Loading...</p>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";

export default {
  name: "AboutView",

  setup() {
    const image = ref("");

    async function loadImage() {
      const data = await fetch(
        "https://images.unsplash.com/photo-1632351459705-22a52c7a3d1d?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8N3x8ZmV0Y2h8ZW58MHx8MHx8&auto=format&fit=crop&w=500&q=60"
      );
      const blob = await data.blob();
      return new Promise((resolve) => {
        const reader = new FileReader();
        reader.readAsDataURL(blob);

        reader.onload = (e) => {
          // const base64data = e.target.result;

          // const result = base64data.replace(
          //   /^data:image\/(png|jpg|jpeg);base64,/,
          //   ""
          // );

          resolve(e.target.result);
        };
      });
    }

    onMounted(async () => {
      image.value = await loadImage();
    });

    return {
      image,
    };
  },
};
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
