<template>
    <div
        ref="tooltip"
        v-html="content"
        :style="{top, left}"
    ></div>
</template>

<script>
  export default {
    name: 'v-simple-tooltip',
    props: ['content'],
    data() {
      return {
        top: 0,
        left: 0
      }
    },
    mounted() {
      // определяем координаты родительского объекта
      const top = this.$el.parentNode.getBoundingClientRect().top;
      const left = this.$el.parentNode.getBoundingClientRect().left;

      // определяем длину и ширину родительского объекта
      const parent_height = this.$el.parentNode.offsetHeight;
      const parent_width = this.$el.parentNode.offsetWidth;

      // определяем координаты блока подсказки
      const tooltip_top = top + pageYOffset + parent_height;
      const tooltip_left = left + pageXOffset + parent_width;

      // задаём нужные свойства компоненту
      this.top = tooltip_top + 'px';
      this.left = tooltip_left + 'px';
    }
  };
</script>

<style scoped>
    div {
        position: absolute;
        width: 400px;
        background: white;
        border: 1px solid #AAAAAA;
        padding: 10px;
    }
</style>
