<template>
  <v-col cols="12" sm="12" md="12" lg="6" xl="6" :class="$style.container">
    <div :class="$style.cat_unit">
      <img
        :class="[
          $style.cat_img,
          { [$style.small]: $vuetify.breakpoint.mdAndDown },
        ]"
        :src="cat.url"
        :alt="cat.uuid"
      />
      <div :class="$style.figure">
        <div>
          <span :class="$style.figure1">撮影場所：</span>
          <span>{{ cat.address }}</span>
        </div>
        <div>
          <span :class="$style.figure2">撮影日：</span>
          <span>{{ cat.createDate | moment }}</span>
        </div>
      </div>
    </div>
  </v-col>
</template>

<script>
export default {
  props: {
    cat: {
      type: Object,
      default: null,
    },
  },
}
</script>

<style lang="scss" module>
.container {
  display: flex;
  flex-flow: column;
  align-items: center;
  border-bottom: 1px solid #ddd;
  .cat_unit {
    .cat_img {
      text-align: center;
      max-width: 100%;
      height: 500px;
      margin-bottom: 15px;
      object-fit: contain;
      &.small {
        height: unset;
        max-height: 500px;
      }
    }
    .figure {
      width: fit-content;
      margin: 0 auto;
      .figure1 {
        font-weight: bold;
        width: 80px;
        display: inline-block;
      }
      .figure2 {
        font-weight: bold;
        width: 80px;
        display: inline-block;
      }
    }
  }
}
</style>
