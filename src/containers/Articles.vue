<template>
  <div>
    <div class="uk-section">
      <div class="uk-container uk-container-large">
        <h1>Connie's Photography Blog</h1>

        <ArticlesList :articles="articles"></ArticlesList>
      </div>
    </div>
  </div>
</template>

<script>
import ArticlesList from "../components/ArticlesList.vue";
import gql from "graphql-tag";

export default {
  components: {
    ArticlesList
  },
  data() {
    return {
      articles: []
    };
  },
  apollo: {
    articles: gql`
      query Articles {
        articles {
          id
          title
          media {
            url
          }
          published_at
          category {
            name
          }
        }
      }
    `
  }
};
</script>