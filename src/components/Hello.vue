<template>
  <div class="layout-padding row justify-center">
    <q-btn
      round
      color="blue-3"
      class="fixed-top-right"
      style="margin: 30px 30px 0 0"
    >
      <q-icon name="edit" />
      <q-tooltip anchor="bottom middle" self="top middle" :offset="[10, 10]">
        写出你的困惑，试试看！
      </q-tooltip>
    </q-btn>
    <div style="width: 500px; max-width: 90vw;">
      <p class="caption">解忧杂货店</p>
      
      <br>
      <q-infinite-scroll :handler="refresher">
        <p v-for="(item, index) in items" v-bind:key="index" class="caption">
          <q-card inline >
            <q-card-title>
              Title
              <span slot="subtitle">Subtitle</span>
              <q-icon slot="right" name="alarm" />
            </q-card-title>
            <q-card-main>
              测试内容啊啊啊啊手机壳大时代
              测试内容啊啊啊啊手机壳大时代
              测试内容啊啊啊啊手机壳大时代
              测试内容啊啊啊啊手机壳大时代
            </q-card-main>
            <q-card-separator />
            <q-card-actions>
              <q-btn flat>Action 1</q-btn>
              <q-btn flat>Action 2</q-btn>
            </q-card-actions>
          </q-card>
        </p>
        <div class="row justify-center" style="margin-bottom: 50px;">
          <q-spinner-dots slot="message" :size="40" />
        </div>
      </q-infinite-scroll>
    </div>
    <q-btn
      v-back-to-top
      round
      color="blue-3"
      class="fixed-bottom-right"
      style="margin: 0 30px 30px 0"
    >
      <q-icon name="keyboard_arrow_up" />
    </q-btn>
  </div>
</template>

<script>
import {
  QInfiniteScroll,
  QChip,
  QSpinnerDots,
  QCard,
  QCardTitle,
  QCardMedia,
  QCardActions,
  QCardSeparator,
  QCardMain,
  QBtn,
  QIcon,
  BackToTop,
  Ripple,
  QTooltip
} from 'quasar'

export default {
  components: {
    QIcon,
    QBtn,
    QCard,
    QCardTitle,
    QCardMedia,
    QCardActions,
    QCardSeparator,
    QCardMain,
    QInfiniteScroll,
    QChip,
    QSpinnerDots,
    QTooltip
  },
  directives: {
    BackToTop,
    Ripple
  },
  data () {
    return {
      items: [{}, {}, {}, {}, {}]
    }
  },
  methods: {
    refresher (index, done) {
      setTimeout(() => {
        let items = []

        for (let i = 0; i < 7; i++) {
          items.push({})
        }

        this.items = this.items.concat(items)
        done()
      }, 2500)
    }
  }
}
</script>

<style lang="styl">
@import '~variables'
  .play-backtotop
    color white
    position fixed
    left 0
    top 30%
    padding 15px
    width 90px
    background-color $secondary
    border-radius 0 15px 15px 0
    &:hover
      color $grey-4
</style>