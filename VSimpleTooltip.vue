<template>
    <div
        v-html="content"
        :style="{
            top,
            left,
            ...style
        }"
    ></div>
</template>

<script>
  export default {
    name: 'v-simple-tooltip',
    props: ['content', 'style'],
    data() {
      return {
        parent_top: 0,
        parent_height: 0,

        parent_left: 0,
        parent_width: 0,

        tooltip_height: 0,
        tooltip_width: 0
      }
    },
    computed: {
        top() {
            let tooltip_top = this.parent_top + pageYOffset + this.parent_height;

            // если элемент по высоте выползает за границу экрана
            if( tooltip_top - pageYOffset + this.tooltip_height > document.body.clientHeight ) {
                // отображаем его не снизу, а сверху
                tooltip_top = this.parent_top + pageYOffset - this.tooltip_height - 1;
            }

            return tooltip_top + 'px';
        },
        left() {
            let tooltip_left = this.parent_left + pageXOffset + this.parent_width;

            // если элемент по ширине выползает за границу экрана
            if( tooltip_left - pageXOffset + this.tooltip_width > document.body.clientWidth ) {
                // отображаем его не справа, а слева
                tooltip_left = this.parent_left + pageXOffset - this.tooltip_width - 1;
            }

            return tooltip_left + 'px';
        }
    },
    mounted() {
        this.parent_top = this.$el.parentNode.getBoundingClientRect().top;
        this.parent_height = this.$el.parentNode.offsetHeight;

        this.parent_left = this.$el.parentNode.getBoundingClientRect().left;
        this.parent_width = this.$el.parentNode.offsetWidth;

        this.tooltip_height = this.$el.clientHeight;
        this.tooltip_width = this.$el.clientWidth;
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
        z-index: 100;
        border-radius: 5px;
    }
</style>
