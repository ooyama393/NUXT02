<template>
  <layout-wrapper>
    <layout-visual title="404" :height="40" visual="visual-error">
    </layout-visual>
    <p class="text-gray-900 mb-20 text-lg text-center">
      お探しのページは存在しません
    </p>
  </layout-wrapper>
</template>

<script>
export default {
  head() {
    return {
      title: 'エラーページ',
    }
  },
}
</script>
