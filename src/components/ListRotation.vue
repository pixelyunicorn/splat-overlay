<template>
  <div class="rotation">
    <div layout="grid" column-count="3">
      <div class="rotation-icon" :style="'background-image:url(./src/assets/'+ schedule.rule.key +'.png)'"><span>{{ schedule.rule.key }}</span></div>
      <div class="rotation-cube" :style="'background-image:url(https://splatoon2.ink/assets/splatnet/'+ schedule.stage_a.image+')'"><span style="background-image: url(./src/assets/sploosh.svg);">{{ shorthand(schedule.stage_a.name) }}</span></div>
      <div class="rotation-cube" :style="'background-image:url(https://splatoon2.ink/assets/splatnet/'+ schedule.stage_b.image+')'"><span style="background-image: url(./src/assets/sploosh.svg);">{{ shorthand(schedule.stage_b.name) }}</span></div>
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
  methods: {
    shorthand: function (name) {
      // there's probably a better way to do this
      switch(name) {
        case "Inkblot Art Academy": return "Academy";
        case "Goby Arena": return "Arena";
        case "Camp Triggerfish": return "Camp";
        case "Snapper Canal": return "Canal";
        case "Kelp Dome": return "Dome";
        case "Musselforge Fitness": return "Fitness";
        case "Ancho-V Games": return "Games";
        case "New Albacore Hotel": return "Hotel";
        case "Shellendorf Institute": return "Institute";
        case "Starfish Mainstage": return "Mainstage";
        case "Arowana Mall": return "Mall";
        case "Manta Maria": return "Manta";
        case "MakoMart": return "Mart";
        case "Skipper Pavilion": return "Pavilion";
        case "Piranha Pit": return "Pit";
        case "Port Mackerel": return "Port";
        case "Humpback Pump Track": return "Pumptrack";
        case "The Reef": return "Reef";
        case "Sturgeon Shipyard": return "Shipyard";
        case "Blackbelly Skatepark": return "Skatepark";
        case "Moray Towers": return "Towers";
        case "Walleye Warehouse": return "Warehouse";
        case "Wahoo World": return "World";
        case "Shifty Station": return "Shifty";
        default: return name;
      }
    }
  }
}
</script>

<style lang="scss">
$spacing-unit: 20px;
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
  box-shadow: inset 0 0 0 8px rgba(0, 0, 0, 0.25);
  border-radius: $border-radius;
  overflow: hidden;

  span {
    position: absolute;
    bottom: 1em;
    left: 0;
    width: 100%;
    height: 4rem;
    line-height: 4rem;
    background-size: cover;
    background-position: right;
    text-align: left;
    color: white;
    font-size: 1.5em;
    padding-left: 8px;
    // padding-right: 3.25em;
    font-weight: bold;
    filter: drop-shadow(4px 4px 10px rgba(25, 25, 25, 0.75));
    -webkit-filter: drop-shadow(4px 4px 10px rgba(25, 25, 25, 0.75));
  }
}
</style>
