<template>
  <Layout>
    <div class="container">
      <div class="hero">
        <h1 class="hero-title">{{ $page.general.title }}</h1>
        <h2 class="hero-subtitle">
          {{ $page.general.subtitle }}
        </h2>
      </div>
      <div class="projects">
        <div
          class="project"
          v-for="item in $page.projects.edges"
          :key="`project${item.node.id}`"
        >
          <g-link class="project-link" :to="`/project/${item.node.id}`">
            <g-image
              class="thumbnail"
              style="width:2560px"
              :src="`${GRIDSOME_API_URL}${item.node.cover[0].url}`"
            />
            <h3 class="project-title">{{ item.node.title }}</h3>
            <div class="categories">
              <span class="category">{{ item.node.categories }}</span>
              <span class="category">{{ item.node.color }}</span>
            </div>
          </g-link>
        </div>
      </div>
    </div>
    <div>
      <div class="latest-journals-heading container">
        <span class="label">Latest and greatest</span>
      </div>
      <div class="latest-journals">
        <div class="container">
          <g-link
            class="journal"
            v-for="item in $page.journals.edges"
            :key="`journal${item.node.id}`"
            :to="`/journal/${item.node.id}`"
          >
            <h3 class="journal-title">
              {{ item.node.title }}
            </h3>
          </g-link>
        </div>
      </div>
    </div>
  </Layout>
</template>
<page-query>
query{
  journals:allStrapiJournals{
    edges{
      node{
        id
        title
      }
    }
  }
  projects:allStrapiProjects{
    edges{
      node{
        id
        title
        color
        categories
        cover{
          url
        }
      }
    }
  }
  general:strapiGeneral(id:1){
    title
    subtitle
  }
}
</page-query>
<script>
export default {
  name: "IndexPage",
  metaInfo: {
    title: "Hello, world!",
  },
};
</script>

<style scoped>
.home-links a {
  margin-right: 1rem;
}

.journal {
  flex: 0 0 100%;
  display: block;
  padding: 2rem;
  transition: background 0.25s ease;
  text-decoration: none;
  border-bottom: 1px solid var(--color-base-1);
}
.journal:last-of-type {
  border-bottom: 0;
}
.journal:hover {
  background: var(--color-base-1);
}
.journal-title {
  font-size: 1rem;
  line-height: 1.35;
}
.latest-journals-heading {
  margin-top: 6rem;
  margin-bottom: 1rem;
  font-size: 0.6rem;
  font-weight: 400;
  text-transform: uppercase;
}
.latest-journals {
  max-width: 100%;
  margin: 0 2rem;
  border: 1px solid var(--color-base-1);
}
.latest-journals .container {
  display: flex;
  flex-wrap: wrap;
}

@media (min-width: 580px) {
  .journal {
    flex: 0 0 50%;
  }
  .journal:first-child {
    border-right: 1px solid var(--color-base-1);
  }
  .journal:first-child,
  .journal:nth-child(2) {
    border-bottom: 1px solid var(--color-base-1);
  }
  .journal:nth-child(3) {
    border-right: 1px solid var(--color-base-1);
    border-bottom: 0;
  }
}
@media (min-width: 920px) {
  .journal {
    flex: 0 0 25%;
  }
  .journal:first-child,
  .journal:nth-child(2),
  .journal:nth-child(3) {
    border: 0;
    border-right: 1px solid var(--color-base-1);
  }

  .latest-journals {
    margin: 0;
    border-left: 0;
    border-right: 0;
    border-top: 1px solid var(--color-base-1);
    border-bottom: 1px solid var(--color-base-1);
  }
}

.projects {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 4rem;
}
.project {
  grid-column: auto/span 2;
  text-align: center;
}
.project-link {
  text-decoration: none;
}
.thumbnail {
  height: 560px;
  -o-object-fit: cover;
  object-fit: cover;
  transition: all 0.15s ease;
  box-shadow: 0 0 40px -20px rgba(0, 0, 0, 0.25);
}
.project-title {
  font-size: 1rem;
  color: var(--color-contrast);
  margin: 2rem 0 1rem;
}
.categories {
  font-size: 0.8rem;
  color: var(--color-contrast-1);
}
.category {
  margin-right: 0.8rem;
}
.category:last-of-type {
  margin: 0;
}
.project:hover .thumbnail {
  transform: scale(1.02);
  box-shadow: 0 20px 40px -20px rgba(0, 0, 0, 0.25);
}
@media (min-width: 920px) {
  .project {
    grid-column: auto/span 1;
  }
  .project:nth-child(3n + 1) {
    grid-column: auto/span 2;
  }
}
</style>
