<template>
  <div class="w-full sm:w-1/2 lg:w-1/3 xl:w-1/4">
    <a
      class="box resource-box pb-3"
      :href="link"
      :style="{background: color}"
      @mouseover="hovered = true"
      @mouseleave="hovered = false"
    >
      <figure class="resource-icon">
        <img
          class="icon"
          :src="iconFileName"
          style="filter: brightness(0) invert(1);"
        />
      </figure>
      <transition name="slide-out" mode="out-in">
        <div v-if="!hovered" class="resource-title">{{ title }}</div>
      </transition>
      <transition name="slide-in">
        <div v-show="hovered" class="resource-desc">{{ desc }}</div>
      </transition>
    </a>
  </div>
</template>

<script>
export default {
  name: 'ResourceGridItem',
  props: {
    link: {
      type: String,
      required: true,
    },
    iconFileName: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    desc: {
      type: String,
      required: true,
    },
    color: {
      type: String,
      required: false,
      default: '#11991c',
    },
  },
  data() {
    return {
      hovered: false,
    }
  },
}
</script>

<style scoped>
a {
  text-decoration: none !important;
  min-height: 148px;
  margin: 0 !important;
}

.box {
  background-color: #fff;
  border-radius: 6px;
  color: #4a4a4a;
  display: block;
  padding: 1.25rem;
  min-width: 156px;
}

.box.resource-box {
  height: 230px;
  transition: all 0.2s ease-in-out;
  flex: 1 0 21%;
  margin: 5px !important;
}

.box.resource-box:hover {
  opacity: 0.75;
}

.resource-icon {
  margin-bottom: 32px;
  display: block;
  height: 42px;
  width: 42px;
  margin-left: 0;
  font-size: 50px !important;
  color: #fff;
  margin-top: unset;
}

.icon {
  height: 56px;
  width: 56px;
  color: #fff;
}

.resource-title {
  font-size: 24px;
  color: #fff;
  font-weight: 500;
  word-wrap: break-word;
  line-height: 1.2em;
  position: absolute;
  max-width: 72%;
}

.resource-title-hovered {
  font-size: 16px;
  color: #fff;
}

.resource-desc {
  font-size: 18px;
  color: #fff;
  font-weight: 300;
  max-width: 100%;
}

.slide-out-enter-active {
  transition: all 0.3s ease-out;
}

.slide-out-leave-active {
  transition: all 0.3s ease-out;
}

.slide-out-enter,
.slide-out-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(-20px);
  opacity: 0;
}

.slide-in-enter-active {
  transition: all 0.3s ease-out;
}

.slide-in-leave-active {
  transition: all 0.3s ease-out;
}

.slide-in-enter,
.slide-in-leave-to {
  /* .slide-fade-leave-active below version 2.1.8 */
  transform: translateX(20px);
  opacity: 0;
}

.slide-in-enter-to,
.slide-in-leave {
  /* .slide-fade-leave-active below version 2.1.8 */

  /* transform: translateX(-20px); */
  opacity: 1;
}
</style>
