<template>
  <div class="rotation">
    <div layout="grid" column-count="3">
      <div class="rotation-icon" :style="'background-image:url(./src/assets/'+ schedule.rule.key +'.svg)'"><span>{{ schedule.rule.key }}</span></div>
      <div class="rotation-cube" :style="'background-image:url(https://splatoon2.ink/assets/splatnet/'+ schedule.stage_a.image+')'"><span style="background-image: url(./src/assets/sploosh.svg);">{{ schedule.stage_a.name }}</span></div>
      <div class="rotation-cube" :style="'background-image:url(https://splatoon2.ink/assets/splatnet/'+ schedule.stage_b.image+')'"><span style="background-image: url(./src/assets/sploosh.svg);">{{ schedule.stage_b.name }}</span></div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'list-rotation',
  props: ['schedule'],
  data () {
    return {
      schedules: null,
    }
  },

}
</script>

<style lang="scss">
$spacing-unit: 10px;
$border-radius: 6px;
[layout="grid"] {
  display: grid;
  grid-column-gap: $spacing-unit;
  grid-row-gap: $spacing-unit;
}
@for $i from 1 through 6 {
  [column-count="#{$i}"] {
    grid-template-columns: repeat(#{$i}, 1fr);
  }
}
@for $i from 1 through 6 {
  [row-count="#{$i}"] {
    grid-template-rows: repeat(#{$i}, auto);
  }
}

.rotation-icon {
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  span {
    display: none;
  }
  &:hover {
    span {
      display: block;
    }
  }
}

.rotation-cube {
  background: lightGray;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
  width: 200px;
  height: 200px;
  box-shadow: inset 0 0 0 6px rgba(0,0,0,.15);
  border-radius: $border-radius;

  span {
    position: absolute;
    bottom: 1em;
    left: 0;
    width: 100%;
    max-width: 100%;
    height: 3em;
    line-height: 3em;
    background-size: cover;
    background-position: right;
    text-align: left;
    color: white;
    padding-left: .5em;
    // padding-right: 3.25em;
    font-weight: bold;
    filter: drop-shadow(2px 4px 4px rgba(0,20,70,.75));
    -webkit-filter: drop-shadow(2px 4px 4px rgba(0,20,70,.75));
  }
}
</style>
