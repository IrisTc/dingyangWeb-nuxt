<template>
    <div>
      <article-view :type="'research'" :articles="article" :id-init="id"></article-view>
    </div>
</template>
<script>
import ArticleView from '~/components/Article'
import axios from "~/plugins/axios";
export default {
    components: {
        ArticleView
    },
    props: ['id'],
    data() {
      return {
        article: [],
      }
    },
    async asyncData (params) {
      const result = await axios.get(params.app.host +"/api/dingyang/article?type=research");
      const articles = result.data.result
      return {
        article : articles
      }
    }
}
</script>