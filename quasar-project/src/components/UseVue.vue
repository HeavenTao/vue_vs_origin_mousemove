<template>
  <div style="position:relative">
    <div v-bind:style="style" v-on:mousedown="mousedown"></div>
  </div>
</template>

<script>
export default {
  name: "UseVue",
  computed: {
    style: function () {
      return {
        width: 100 + 'px',
        height: 100 + 'px',
        backgroundColor: "lightgreen",
        position: "absolute",
        left: this.x + 'px',
        top: this.y + 'px'
      }
    }
  },
  data: function () {
    return {
      x: 0,
      y: 0,
      backup: {
        x: 0,
        y: 0
      },
      startPoint: null,
      drag: false
    }
  },
  methods: {
    mousedown: function (e) {
      console.log(e)
      this.backup = {
        x: this.x,
        y: this.y
      }
      this.startPoint.x = e.clientX;
      this.startPoint.y = e.clientY;

      document.addEventListener("mousemove", this.mousemove);
      document.addEventListener("mouseup", this.mouseup);

      this.drag = true;
    },
    mousemove: function (e) {
      if (this.drag) {

      }
    },
    mouseup: function () {
      document.removeEventListener("mousemove", this.mousemove);
      document.removeEventListener("mouseup", this.mouseup);
    }
  }
}
</script>
