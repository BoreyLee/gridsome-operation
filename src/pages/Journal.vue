<template>
  <Layout>
    <div class="container">
      <div class="journal-hero">
        <h1 class="journal-header">
          a wise person once said...
        </h1>
      </div>
    </div>
    <g-link
      v-for="item in $page.journals.edges"
      :key="`journal${item.node.id}`"
      :to="`/journal/${item.node.id}`"
      class="journal-post"
      ><div class="container journal">
        <h2 class="journal-title">
          {{ item.node.title }}
        </h2>
        <p class="journal-excerpt">
          {{ item.node.subtitle }}
        </p>
      </div>
    </g-link>
  </Layout>
</template>
<page-query>
query{
  journals:allStrapiJournals{
    edges{
      node{
        id
        title
        date
        subtitle
      }
    }
  }
}
</page-query>
<script>
export default {
  name: "JournalPage",
  metaInfo: {
    title: "Journal",
  },
};
</script>

<style scoped>
.journal-title {
  font-size: 2rem;
  color: var(--color-contrast);
}
.journal-excerpt {
  color: var(--color-contrast-1);
}
@media (min-width: 560px) {
  .journal-post {
    padding: 3rem 0;
  }
}
@media (min-width: 860px) {
  .journal-post {
    padding: 5rem 0;
  }
  .container {
    padding: 0 6rem;
  }
}
</style>
