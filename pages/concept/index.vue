<template>
  <layout-wrapper>
    <layout-visual
      title="ああああConcept"
      :height="40"
      visual="visual-concept"
    />
    <div class="w-full md:max-w-3xl mx-auto pt-20 px-6 md:px-0">
      <h3 class="text-2xl text-red-800 font-extrabold mb-5 text-center">
        h3h3hh3
      </h3>
      <div class="clearfix p-4 mb-10">
        <img
          class="float-right ml-4 my-2 h-56"
          src="~/assets/img/concept.jpg"
        />
        <div>
          <p class="mb-5">一つ目の段落</p>
          <p class="mb-5">二つ目の段落</p>
        </div>
      </div>
      <base-button name="トップへ戻る" link="/" />
    </div>
  </layout-wrapper>
</template>

<script>
export default {
  head() {
    return {
      title: 'concon',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'コンセプトページのディスクリプション',
        },
      ],
    }
  },
}
</script>
