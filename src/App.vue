<template>
  <div class="wrapper">
    <header>
      <a class="brand" href="/">
      <h1>Ultimate scores</h1>
      <img src="" alt="">
      </a>
    
      <nav>

      </nav>
    </header>
    <aside>Sidebar</aside>
    <main>
      <section class="card-list">
          <card-component v-for="m in items" :key="m.id"
          :match="m.title"
          :video="m.videos[0].embed"
          :competition="m.competition.name"
          :thumb="m.thumb"/>
      </section>
      
    </main>
    <footer>Footer</footer>
  </div>
</template>

<script>
import CardComponent from './components/CardComponent.vue'

export default {
  components: { CardComponent },
  name: 'App',
  data() {
    return {
      items: []
    }
  },
  async beforeMount () {
        const f = await fetch(`https://www.scorebat.com/video-api/v1/`);
        const data = await f.json();
        console.log(data);
        this.items = data;
        console.log(this.items)
  },

}
</script>



<style lang="scss">
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  @import url('https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,400;0,700;1,300&display=swap');

  :root {
    --primary-color: #6B71D0;
    --secondary-color: #85FFC7;
    --button-color: #FF8552;
    --thirdary-color: #E6E6E6;
    --text-color: #39393A;
    --body-bg: #E6E6E6;
  }

  body,
  html {
    height: 100%;
  }
  body {
    background-color: var(--body-bg);
    font-family: 'Lato', sans-serif;
  }

  a {
    text-decoration: none;
    color: var(--primary-color);
  }

  .wrapper {
    display: grid;
    grid-template-columns: 20em auto;
    grid-template-rows: auto;

    aside,
    main {
      grid-column-start: 1;
      grid-column-end: 4;

    }
    aside {
      @media screen and (min-width: 1024px) {
        grid-column-start: 1;
        grid-column-end: 2;
      }
    }
    main {
      padding: 1rem;
      @media screen and (min-width: 1024px) {
        grid-column-start: 2;
        grid-column-end: 4;
      }
    }

    header,
    footer {
      grid-column-start: 1;
      grid-column-end: 4;
    }
    // Header Styling
    header {
      background: var(--primary-color);
      padding: 1rem;
      color: var(--thirdary-color);
    }

    .brand {
      color: var(--thirdary-color);
    }

    .card-list {
      display: grid;
      gap: 1rem;

      @media screen and (min-width: 1024px) {
        grid-template-columns: repeat(2, 1fr);
      }
      @media screen and (min-width: 1400px) {
        grid-template-columns: repeat(3, 1fr);
      }
    }
  }
</style>
