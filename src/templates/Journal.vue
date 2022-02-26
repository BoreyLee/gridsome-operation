<template>
  <Layout>
    <div class="journal">
      <div class="container journal-container">
        <div class="journal-header">
          <h1 class="journal-title">
            {{ $page.journal.title }}
          </h1>
          <div class="journal-meta">
            <div class="journal-author">
              <span class="label">Author</span
              ><span class="author-name">{{ $page.journal.author }}</span>
            </div>
            <div class="journal-date">
              <span class="label">Date</span>
              <div>{{ $page.journal.date }}</div>
            </div>
            <div class="journal-time">
              <span class="label">Time</span
              ><span>{{ $page.journal.created_at }}</span>
            </div>
          </div>
        </div>
        <div
          class="journal-content"
          v-html="mdToHtml($page.journal.content)"
        ></div>
      </div>
    </div>
  </Layout>
</template>

<page-query>
query($id: ID!){
  journal:strapiJournals(id:$id){
    id
    title
    author
    date
    created_at
    content
  }
}
</page-query>
<script>
import MarkdownIt from "markdown-it";
const md = new MarkdownIt();
export default {
  name: "Journal",
  metaInfo: {
    title: "Journal",
  },
  methods: {
    mdToHtml(str) {
      return md.render(str);
    },
  },
};
</script>

<style scoped></style>
