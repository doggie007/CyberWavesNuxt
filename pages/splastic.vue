<template>
  <div id="map">
    <v-overlay :value="isSimulating">
      <v-card dark class="pa-5 text-center">
        <v-flex class="mx-auto">
          <v-progress-circular
            indeterminate
            color="primary"
            v-if="isSimulating"
          >
          </v-progress-circular>
        </v-flex>
        <p class="text-subtitle-1 mt-4">Calculating...</p>
      </v-card>
    </v-overlay>

    <!-- <div class="right-card">
      <v-container class="pa-2">
        <v-row>
          <input type="checkbox" id="checkbox" v-model="checked" />
          <label for="checkbox">Heatmap?</label>
        </v-row>
        <v-row class="justify-end">
          <v-btn light elevation="2"> Simulate </v-btn>
        </v-row>
      </v-container>
    </div> -->
    <div class="right-card">
      <v-card class="ma-5" width="300">
        <v-container class="pa-8">
          <v-row>
            <v-col style="display: inline-flex; align-items: center">
              <span class="text-h6 font-weight-light">DURATION </span>
            </v-col>
            <!-- <v-col >
             </v-col> -->

            <v-col
              class="text-end text-subtitle-1 font-weight-bold"
              style="display: inline-flex; align-items: center"
            >
              <div style="position: sticky">
                <span>{{ sliderDuration / 30 }}</span>
                <span>months</span>
              </div></v-col
            >
          </v-row>
          <v-row>
            <div class="py-1"></div>
          </v-row>
          <!-- <v-row>
            <input type="checkbox" id="checkbox" v-model="checked" />
            <label for="checkbox">Heatmap?</label>
          </v-row> -->
          <v-row class="justify-center">
            <v-slider
              step="180"
              min="180"
              ticks
              max="1080"
              dense
              hide-details
              v-model="sliderDuration"
            >
            </v-slider>
          </v-row>
          <v-row class="justify-center">
            <v-switch
              color="indigo"
              :label="`${forwardsMessage}`"
              v-model="forwards"
            ></v-switch>
          </v-row>
          <v-row class="justify-center">
            <v-btn
              light
              elevation="2"
              v-if="!hasSimulated"
              @click="simulateParticles()"
            >
              Simulate
            </v-btn>
            <v-btn light elevation="2" v-if="hasSimulated" @click="reset()">
              Reset
            </v-btn>
          </v-row>
        </v-container>
      </v-card>
    </div>
    <div id="left" class="sidebar flex-center left collapsed">
      <div class="sidebar-content rounded-rect flex-center">
        <div>
          <v-container class="pa-5 text-center overflow-auto">
            <v-row class="text-left">
              <v-col
                ><NuxtLink to="/">
                  <v-avatar tile class="mr-3" color="grey lighten-5" size="70">
                    <v-img
                      eager
                      contain
                      :src="require('static/cyberwaves-full-logo.png')"
                    ></v-img>
                  </v-avatar> </NuxtLink
              ></v-col>
              <v-col class="text-h3 font-weight-bold text-uppercase text-left">
                Splastic
              </v-col>
            </v-row>
            <v-row>
              <v-divider></v-divider>
            </v-row>
            <v-row>
              <v-col class="text-justify text-subtitle-2 font-weight-regular">
                Splastic simulates the trajectory of plastic pollution over a
                duration of time using real world oceanographic data and
                physical equations.
                <br />
                This information can be used for coastal cleanup organisations
                and investigative purposes, and serves as public education on
                ocean pollution.
                <br />
                <br />
                Note that ocean circulation is fundamentally a chaotic system,
                while the model is deterministic.
              </v-col>
            </v-row>
            <v-row>
              <v-col class="text-left">
                <v-divider class="mb-3"></v-divider>
                <p class="text-h6">How to use</p>
                <p class="text-subtitle-1 blue--text font-weight-bold">
                  Click on anywhere in the ocean to "place" the plastic patches,
                  specify the duration to simulate the path backwards or
                  forwards in time, then click simulate!
                </p>
              </v-col>
            </v-row>
            <!-- <v-row>
              <v-col class="text-left">
                <v-divider class="mb-3"></v-divider>
                <p class="text-h6">Share this map</p>

                <div>
                  <v-icon>mdi-facebook</v-icon>
                  <v-icon>mdi-instagram</v-icon>
                  <v-icon>mdi-whatsapp</v-icon>
                  <v-icon>mdi-github</v-icon>
                </div>

                <v-divider class="mt-3"></v-divider>
              </v-col>
            </v-row> -->
            <v-row>
              <v-col class="text-left">
                <v-divider class="mb-3"></v-divider>
                <p class="text-h6">Credits</p>
                <a href="https://ocean.ust.hk:8443/SiteMapApi/new/index.jsp"
                  >Hong Kong Universtiy of Science and Technology</a
                >
                <br />
                <a href="https://oceanparcels.org/">Ocean Parcels</a>

                <v-divider></v-divider>
              </v-col>
            </v-row>
          </v-container>
        </div>

        <div class="sidebar-toggle special-rect left" @click="toggleSidebar">
          <!-- &rarr; -->
          <svg
            width="0.4em"
            height="0.4em"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 8 10"
            style="display: block"
            :class="{ svgCollapsed: collapsed }"
          >
            <path fill-rule="evenodd" d="M7.13.473L.343 5 7.13 9.527z"></path>
          </svg>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
#map {
  width: 100%;
  height: 100vh;
}

.right-card {
  position: absolute;
  z-index: 2;
  right: 0;
  bottom: 0;
}

.svgCollapsed {
  transform: scale(-1, 1);
}

.rounded-rect {
  background: white;
  border-radius: 7px;
  box-shadow: 0 0 50px -25px black;
}

.special-rect {
  background: white;
  border-top-right-radius: 12px;
  border-bottom-right-radius: 12px;
  box-shadow: 0 0 50px -25px black;
}

.flex-center {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
}

.flex-center.left {
  left: 0px;
}

.flex-center.right {
  right: 0px;
}

.sidebar-content {
  position: absolute;
  width: 98%;
  height: 98%;
  margin-right: 20px;
  /* font-family: Arial, Helvetica, sans-serif;
  font-size: 32px;
  color: gray; */
}

.sidebar-toggle {
  font-size: 32px;
  opacity: 0.6;
  position: absolute;
  width: 0.8em;
  height: 1.1em;
  overflow: visible;
  display: flex;
  justify-content: center;
  align-items: center;
}

.sidebar-toggle.left {
  right: -0.8em;
}

.sidebar-toggle:hover {
  opacity: 0.9;
  cursor: pointer;
}

.sidebar {
  transition: transform 1s;
  z-index: 100;
  width: 360px;
  height: 100%;
}

/*
The sidebar styling has them "expanded" by default, we use CSS transforms to push them offscreen
The toggleSidebar() function removes this class from the element in order to expand it.
*/
.left.collapsed {
  transform: translateX(-350px);
}
</style>

<script>
import mapboxgl from 'mapbox-gl'
import 'mapbox-gl/dist/mapbox-gl.css'
import MapboxDraw from '@mapbox/mapbox-gl-draw'
import '@mapbox/mapbox-gl-draw/dist/mapbox-gl-draw.css'

export default {
  layout: 'play',
  data() {
    return {
      access_token:
        'pk.eyJ1IjoiamFtZXMwMDdsb2wiLCJhIjoiY2xjdG5oMjl2MGYxeTN2cXR1dTJwaXpuYyJ9.YVYqI-cIgJhczD4h2407Cw',
      map: {},
      center: [114.1694, 22.3193],
      collapsed: true,
      isSimulating: false,
      hasSimulated: false,

      sliderDuration: 180, // in days
      forwards: false,

      sources: [], // store all ids of the sources
    }
  },
  mounted() {
    this.createMap()
  },
  computed: {
    forwardsMessage() {
      return this.forwards ? 'Forwards in time' : 'Backwards in time'
    },
    durationMessage() {
      return this.sliderDuration === 1 ? 'year' : 'years'
    },
  },
  methods: {
    toggleSidebar() {
      this.collapsed = !this.collapsed
      const elem = document.getElementById('left')
      // Add or remove the 'collapsed' CSS class from the sidebar element.
      // Returns boolean "true" or "false" whether 'collapsed' is in the class list.
      const collapsed = elem.classList.toggle('collapsed')
      const padding = {}
      // 'id' is 'right' or 'left'. When run at start, this object looks like: '{left: 300}';
      padding.left = collapsed ? 0 : 300 // 0 if collapsed, 300 px if not. This matches the width of the sidebars in the .sidebar CSS class.
      // Use `map.easeTo()` with a padding option to adjust the map's center accounting for the position of sidebars.

      this.map.easeTo({
        padding,
        duration: 500, // In ms. This matches the CSS transition duration property.
      })
    },
    reset() {
      // remove drawing
      this.draw.deleteAll()
      // remove endpoints and lines
      this.sources.forEach((source) => {
        this.map.removeLayer(source)
        this.map.removeSource(source)
      })
      // empty sources
      this.sources = []
      this.hasSimulated = false
    },
    getPoints() {
      const data = this.draw.getAll()
      console.log(data)
      const coords = data.features.map((obj) => {
        return obj.geometry.coordinates
      })
      console.log(coords)
      //   [[lon, lat]]
      return coords
    },
    createMap() {
      mapboxgl.accessToken = this.access_token

      const bounds = [
        [112.304438, 20.892579], // southwest coords
        [115.6811, 23.1279], // northeast coords
      ]
      this.map = new mapboxgl.Map({
        container: 'map',
        style: 'mapbox://styles/james007lol/cl797cotb000214rrhdkv7byt',
        zoom: 9,
        center: this.center,
        attributionControl: false,
        maxBounds: bounds,
      })

      this.map.on('load', () => {
        // Weird hotfix
        this.toggleSidebar()
        this.toggleSidebar()
      })

      const LotsOfPointsMode = {}

      // When the mode starts this function will be called.
      // The `opts` argument comes from `draw.changeMode('lotsofpoints', {count:7})`.
      // The value returned should be an object and will be passed to all other lifecycle functions
      LotsOfPointsMode.onSetup = function (opts) {
        const state = {}
        state.count = opts.count || 0
        return state
      }

      // Whenever a user clicks on the map, Draw will call `onClick`
      LotsOfPointsMode.onClick = function (state, e) {
        // `this.newFeature` takes geojson and makes a DrawFeature
        const point = this.newFeature({
          type: 'Feature',
          properties: {
            count: state.count,
          },
          geometry: {
            type: 'Point',
            coordinates: [e.lngLat.lng, e.lngLat.lat],
          },
        })
        this.addFeature(point) // puts the point on the map
      }

      // Whenever a user clicks on a key while focused on the map, it will be sent here
      LotsOfPointsMode.onKeyUp = function (state, e) {
        if (e.keyCode === 27) return this.changeMode('simple_select')
      }

      // This is the only required function for a mode.
      // It decides which features currently in Draw's data store will be rendered on the map.
      // All features passed to `display` will be rendered, so you can pass multiple display features per internal feature.
      // See `styling-draw` in `API.md` for advice on making display features
      LotsOfPointsMode.toDisplayFeatures = function (state, geojson, display) {
        display(geojson)
      }

      this.draw = new MapboxDraw({
        defaultMode: 'lots_of_points',
        displayControlsDefault: false,
        userProperties: true,
        modes: Object.assign(
          {
            lots_of_points: LotsOfPointsMode,
          },
          MapboxDraw.modes
        ),
        styles: [
          {
            id: 'gl-draw-point',
            type: 'circle',
            filter: ['all', ['==', '$type', 'Point']],
            paint: {
              'circle-radius': 4,
              'circle-color': '#ffa500',
            },
          },
        ],
      })

      this.map.addControl(this.draw, 'top-right')

      this.map.addControl(
        new mapboxgl.AttributionControl({ compact: true }),
        'bottom-left'
      )
      this.map.addControl(new mapboxgl.NavigationControl(), 'top-left')
    },
    async simulateParticles() {
      this.hasSimulated = true

      this.isSimulating = true
      const coords = this.getPoints()
      const json = JSON.stringify({
        particles: coords,
      })

      const steps = 1000
      const dt = (this.sliderDuration * 24) / steps

      const res = await this.$axios.$post(
        'https://cyberwaves-backend.herokuapp.com/execute',
        json,
        {
          headers: {
            'Content-Type': 'application/json',
          },
          params: {
            forward: this.forwards,
            time_duration: this.sliderDuration, // in days
            time_delta: dt, // in hours
            output_delta: dt, // in hours; match time_delta
            return_trajectory: true,
          },
        }
      )
      console.log(res)
      this.isSimulating = false
      const trajectories = res.trajectories
      // Add points
      trajectories.forEach((trajectory, index) => {
        const uniqueIdPoint = 'point-' + index
        this.map.addSource(uniqueIdPoint, {
          type: 'geojson',
          data: {
            type: 'FeatureCollection',
            features: [
              {
                type: 'Feature',
                geometry: {
                  type: 'Point',
                  coordinates: trajectory[trajectory.length - 1],
                },
              },
            ],
          },
        })

        // Add points layer
        this.map.addLayer({
          id: uniqueIdPoint,
          type: 'circle',
          source: uniqueIdPoint,
          paint: {
            'circle-radius': 4,
            'circle-color': '#ff0000',
          },
        })

        const uniqueIdTrace = 'trace-' + index

        this.sources.push(uniqueIdPoint)
        this.sources.push(uniqueIdTrace)
        // Add trace
        this.map.addSource(uniqueIdTrace, {
          type: 'geojson',
          data: {
            type: 'Feature',
            properties: {},
            geometry: {
              type: 'LineString',
              coordinates: trajectory,
            },
          },
        })
        // Path layer
        this.map.addLayer({
          id: uniqueIdTrace,
          type: 'line',
          source: uniqueIdTrace,
          layout: {
            'line-join': 'round',
            'line-cap': 'round',
          },
          paint: {
            'line-color': 'yellow',
            'line-opacity': 0.5,
            'line-width': 1,
          },
        })
      })
    },
  },
  head() {
    return {
      title: 'Splastic',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            'Splastic tracks and visualises the movement of ocean plastic patches via ocean current models.',
        },
      ],
    }
  },
}
</script>
