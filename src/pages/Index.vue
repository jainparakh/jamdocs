<template>
  <Layout :sidebar="false">
    <div class="content">
      <h3><g-image src="~/assets/img/memoji.png" alt="home-img"/></h3>
      <h1>{{ $static.metadata.siteName }}</h1>
      <nav>
        <!-- To use other icons here, you need to import them in the Shortcut component -->
        <Shortcut link="/about-me" text="About Me" icon="play-icon" />
        <Shortcut link="https://twitter.com/jainparakh" text="Twitter" icon="twitter-icon" />
        <Shortcut link="https://linkedin.com/in/jainparakh/" text="LinkedIn" icon="linkedin-icon" />
      </nav>
    </div>
  </Layout>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
import GitLink from '~/components/GitLink.vue'
import Shortcut from '~/components/Shortcut.vue'

export default {
  components: {
    GitLink,
    Shortcut
  },
  data() {
    return {
      description: 'Home'
    }
  },
  metaInfo() {
    return {
      title: this.description,
      meta: [
        { key: 'description', name: 'description', content: 'The personal website for Parakh Jain' }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.content {
  display: flex;
  flex-direction: column;
}

h1 {
  text-align: center;
  max-width: 600px;
  margin: 1.5em auto 1.5em;
  margin-top: 0;

  @include respond-above(md) {
    max-width: 1000px;
  }
}

h2 {
  font-size: 1.4rem;
  margin: 0;
}

h3 {
  display: block;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 0;
  margin-top: 0;

  img {
    height: 150px;
    width: auto;
  }
}

nav {
  display: flex;
  justify-content: space-between;
  flex-direction: column;

  @include respond-above(sm) {
    flex-direction: row;
  }
}

.git {
  margin: 3em 0 0;
  align-self: center;

  @include respond-above(md) {
    margin: 5em 0 0;
  }
}
</style>
