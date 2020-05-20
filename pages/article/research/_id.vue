<template>
    <div>
      <article-view :type="'research'" :articles="article" :id-init="id"></article-view>
    </div>
</template>
<script>
import ArticleView from '~/components/Article'
import axios from 'axios'
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
    async asyncData () {
      const result = await axios.get("https://admin.dy.tcualhp.cn/api/dingyang/article?type=research");
      const articles = result.data.result
      return {
        article : articles
      }
    }
}
</script>