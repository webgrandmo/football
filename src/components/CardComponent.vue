<template>
<article class="card">
  <section v-html="video"></section>
  <footer class="card__card-footer">
    <h4>Teams:</h4>
    <p>{{ match }}</p>
    <p>Tournament: {{ competition }}</p>
  </footer>
</article>
</template>

<script>
export default {
  name: 'CardComponent',
  props: {
    match: String,
    video: String,
    competition: String,
    thumb: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  :root {
    --primary-color: #6B71D0;
    --secondary-color: #85FFC7;
    --button-color: #FF8552;
    --thirdary-color: #E6E6E6;
    --text-color: #39393A;
    --body-bg: #E6E6E6;
  }
  $text-color: #39393A;
.card {
  background: #fff;
  border: 1px solid lighten($text-color, 50%);
  border-top-left-radius: 6px;
  border-top-right-radius: 6px;

    .card__card-footer {
      padding: .5rem 1rem;
      color: $text-color;
    }
}
</style>
