<template>
  <layout-wrapper>
    <layout-visual
      title="Nuxt infomation/detail"
      :height="40"
      visual="visual-information"
    />

    <div class="w-full md:max-w-3xl mx-auto pt-20 px-6 md:px-0">
      <h2 class="text-xl pb-5 border-b border-gray-500 border-solid font-bold">
        {{ item.title }}
      </h2>
      <div class="pt-4 mb-4">
        <time class="text-gray-700 text-base">{{
          item.date | formatDate
        }}</time>
      </div>
      <!-- eslint-disable-next-line vue/no-v-html -->
      <div class="mb-20" v-html="item.body"></div>
      <base-button name="お知らせへ戻る" link="/information/" />
    </div>
  </layout-wrapper>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData({ params, error }) {
    try {
      const { data } = await axios.get(
        `https://fnucsxfw28.microcms.io/api/v1/news/${params.id}`,
        {
          headers: {
            'X-MICROCMS-API-KEY': '506b1266c068466d83fafbcb8546ace89403',
          },
        }
      )
      return { item: data }
    } catch (err) {
      error({
        errorCode: 404,
      })
    }
  },
  head() {
    return {
      title: this.item.title,
    }
  },
}
</script>
