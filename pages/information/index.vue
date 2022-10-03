<template>
  <layout-wrapper>
    <layout-visual
      style="white-space: pre-wrap"
      title="
      N
        U
         X
           T
                    Information"
      :height="40"
      visual="visual-information"
    />
    <div class="w-full md:max-w-3xl mx-auto pt-20 px-6 md:px-0">
      <layout-information-list
        v-for="(item, index) in items"
        :id="item.id"
        :key="index"
        :date="item.date"
        :title="item.title"
      />
      <base-button name="トップへ戻る" link="/" />
    </div>
  </layout-wrapper>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData() {
    const item = await axios.get('https://fnucsxfw28.microcms.io/api/v1/news', {
      headers: {
        'X-MICROCMS-API-KEY': '506b1266c068466d83fafbcb8546ace89403',
      },
    })
    const items = item.data.contents
    return { items }
  },
  head() {
    return {
      title: 'お知らせ',
    }
  },
}
</script>
