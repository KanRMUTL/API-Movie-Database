<template>
  <b-card
    :title="title"
    :img-src="image"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="mb-2"
  >
    <b-card-text>
      {{ overview }}
    </b-card-text>

    <b-button
      href="#"
      variant="primary"
    >Go somewhere</b-button>
  </b-card>
</template>

<script>
export default {
  name: "Movie",

  props: ["title", "image", "overview"],

  data() {
    return {};
  }
};
</script>
