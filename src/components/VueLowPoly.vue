<template>
 <div class="low-poly-frame" :id="`low-poly-${id}`">
  <img :id="`low-poly-canvas-${id}`">
 </div>
</template>

<script>
import drawTriangles from "./drawTriangles";

const getCanvasSzie = (img, setWidth, setHeight) => {
  let width, height;
  if ((setWidth / img.width) * img.height > setHeight) {
    width = (setHeight / img.height) * img.width;
    height = setHeight;
  } else {
    height = (setWidth / img.width) * img.height;
    width = setWidth;
  }
  return { width, height };
};
export default {
  name: "VueLowPoly",
  data() {
    return {
      id: parseInt(Math.random() * 10000)
    };
  },
  mounted() {
    this.image = document.getElementById(`low-poly-canvas-${this.id}`);
    this.drawCanvas();
  },
  watch: {
    $props: {
      handler() {
        this.drawCanvas();
      },
      deep: true,
      immediate: true
    }
  },
  props: {
    src: {
      type: String,
      default: function() {
        return "";
      }
    },
    width: {
      type: Number,
      default() {
        return 800;
      }
    },
    height: {
      type: Number,
      default() {
        return 600;
      }
    },
    points: {
      type: Number,
      default() {
        return 7500;
      }
    },
    accuracy: {
      type: Number,
      default() {
        return 75;
      }
    },
    grayscale: {
      type: Boolean,
      default() {
        return false;
      }
    }
  },
  components: {},
  methods: {
    async drawCanvas() {
      let img = new Image();
      await new Promise((resolve, reject) => {
        img.addEventListener(
          "load",
          () => {
            resolve();
          },
          false
        );
        img.src = this.src;
      }).then();
      const { width, height } = this;
      const size = getCanvasSzie(img, width, height);
      const newCanvas = await drawTriangles(
        img,
        this.points,
        this.accuracy,
        size.width,
        size.height,
        this.grayscale
      );
      this.image.src = newCanvas.toDataURL();
    }
  }
};
</script>

<style lang="less" scoped>
</style>


