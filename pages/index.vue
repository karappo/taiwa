<template lang="pug">
.container
  img(src="~assets/image/logo.png" srcset="~assets/image/logo.png 1x, ~assets/image/logo@2x.png 2x")
  ExternalLink.help(href="https://docs.google.com/document/d/1wSAPXohNnF5o42wEkVlBjWn9I17vawxKf5gU6_VnKHQ/") 管理マニュアル
  template(v-if="$store.state.gss")
    h3 シートを選択してください
    .sheets
      nuxt-link.sheetLink(v-for="(sheet, idx) in $store.state.gss.sheets" :to="`/${sheet.properties.sheetId}/`" :key="idx" :title="sheet.properties.title") {{ sheet.properties.title }}
  template(v-else)
    h3 エラー：表示可能なシートがありません
</template>

<style lang="sass" scoped>
@import ~assets/style/const
.container
  display: flex
  flex-wrap: wrap
  flex-direction: column
  margin: 30px
  max-width: 420px
.help
  font-size: 14px
  width: auto
  margin: 18px 0 18px auto
h3
  font-size: 18px
  margin: 50px 0 20px 0
.sheets
  width: 100%
.sheetLink
  display: block
  color: #666666
  padding: 20px
  display: block
  align-items: center
  border: 1px solid #707070
  font-size: 16px
  white-space: nowrap
  overflow: hidden
  text-overflow: ellipsis
  &:hover
    background: #E6E6E6
    opacity: 1
.sheetLink + .sheetLink
  margin-top: 12px
</style>

<script>
import { ExternalLink } from '@karappo-inc/vue-components'
export default {
  components: {
    ExternalLink
  }
}
</script>
