<template>
  <div style="position:relative">
    <div ref="el" style="position:absolute;left:0px;top:0px;width:100px;height: 100px;background-color: lightgreen;">
    </div>
  </div>
</template>

<script>
export default {
  name: "UseJs",
  data: function () {
    return {
      backup: {
        x: 0,
        y: 0
      },
      startPoint: {
        x: 0,
        y: 0
      },
      drag: false
    }
  },
  mounted: function () {
    if (this.$refs.el) {
      this.$refs.el.addEventListener("mousedown", this.mousedown)
    }
  },
  methods: {
    mousedown: function (e) {
      var temp = this.getLeftTop();
      this.backup = {
        x: Number(temp.x.replace("px", "")),
        y: Number(temp.y.replace("px", ""))
      }

      this.startPoint.x = e.clientX;
      this.startPoint.y = e.clientY;

      document.addEventListener("mousemove", this.mousemove);
      document.addEventListener("mouseup", this.mouseup);

      this.drag = true;
    },
    mousemove: function (e) {
      if (this.drag) {
        var moveX = e.clientX - this.startPoint.x;
        var moveY = e.clientY - this.startPoint.y;

        var x = this.backup.x + moveX;
        var y = this.backup.y + moveY;

        this.setLeftTop(x, y)
      }
    },
    mouseup: function () {
      this.drag = false;

      document.removeEventListener("mousemove", this.mousemove);
      document.removeEventListener("mouseup", this.mouseup);
    },
    getLeftTop: function () {
      if (this.$refs.el) {
        return {
          x: this.$refs.el.style.left,
          y: this.$refs.el.style.top
        }
      }
    },
    setLeftTop: function (left, top) {
      if (this.$refs.el) {
        this.$refs.el.style.left = left + 'px';
        this.$refs.el.style.top = top + 'px';
      }
    }
  }
}
</script>
