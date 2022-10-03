<template>
  <layout-wrapper>
    <layout-visual title="Nuxt menu" :height="40" visual="visual-menu" />
    <div class="container w-full mx-auto pt-20 pb-20 px-6 md:px-0">
      <div class="mb-20">
        <layout-menu-list
          v-for="(item, index) in contents"
          :key="index"
          :image="item.image"
          :image-url="item.image.url"
          :name="item.name"
          :body="item.body"
          :price="item.price"
        />
      </div>
      <base-button name="トップへ戻る" link="/" />
    </div>
  </layout-wrapper>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData() {
    const test = await axios.get('https://fnucsxfw28.microcms.io/api/v1/menu', {
      headers: {
        'X-MICROCMS-API-KEY': '506b1266c068466d83fafbcb8546ace89403',
      },
    })
    const contents = test.data.contents
    return { contents }
  },
}
</script>
