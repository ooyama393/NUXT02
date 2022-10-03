<template>
  <layout-wrapper>
    <layout-visual title="Nuxt demo" message="Nuxt + microCMS" />

    <div class="box01">
      <p>assets/common.cssからの読み込みテスト</p>
    </div>

    <div class="w-full md:max-w-3xl mx-auto pt-20 px-6 md:px-0">
      <base-heading>menuuu</base-heading>

      <layout-menu-list
        v-for="(item, index) in menuItems"
        :key="index"
        :image="item.image"
        :image-url="item.image.url"
        :name="item.name"
        :body="item.body"
        :price="item.price"
        item-class="md:w-56 mb-20 shadow-lg bg-gray-200"
        block-class="max-w"
        image-class="w-full"
        data-class="px-6 py-4"
        :flag-body="false"
      />

      <div class="mb-10 mx-auto text-center">
        <a
          href="/menu/"
          class="font-semibold md:text-lg xl:text-base px-4 md:px-5 xl:px-4 py-3 md:py-4 xl:py-3 leading-tight shadow-md rounded-lg bg-white hover:bg-gray-200 text-gray-800"
        >
          MENU APIの一覧
        </a>
      </div>
      <h2 class="font-sans text-lg text-gray-800 text-center text-3xl mb-10">
        お知らせ
      </h2>
      <div class="mb-20">
        <layout-information-list
          v-for="(item, index) in infoItems"
          :id="item.id"
          :key="index"
          :date="item.date"
          :title="item.title"
          class="bg-teal-100 border-t-4 border-teal-500 rounded-b text-teal-900 shadow-md mb-5"
        />
      </div>
      <div class="mb-10 mx-auto text-center">
        <a
          href="/information/"
          class="font-semibold md:text-lg xl:text-base px-4 md:px-5 xl:px-4 py-3 md:py-4 xl:py-3 leading-tight shadow-md rounded-lg bg-white hover:bg-gray-200 text-gray-800"
        >
          お知らせの一覧
        </a>
      </div>
    </div>
  </layout-wrapper>
</template>

<script>
import axios from 'axios'
import LayoutInformationList from '../components/LayoutInformationList.vue'
export default {
  components: { LayoutInformationList },
  async asyncData() {
    const menu = await axios.get(
      'https://fnucsxfw28.microcms.io/api/v1/menu?limit=3&filters=flag[equals]true',
      {
        headers: {
          'X-MICROCMS-API-KEY': '506b1266c068466d83fafbcb8546ace89403',
        },
      }
    )
    const info = await axios.get(
      'https://fnucsxfw28.microcms.io/api/v1/news?limit=3',
      {
        headers: {
          'X-MICROCMS-API-KEY': '506b1266c068466d83fafbcb8546ace89403',
        },
      }
    )
    return {
      menuItems: menu.data.contents,
      infoItems: info.data.contents,
    }
  },
}
</script>
