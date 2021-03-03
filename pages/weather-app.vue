<template>
  <v-container>
    <h1 class="display-1 text-center">Weather App</h1>
    <v-flex xs12>
      <v-card color="blue darken-1">
        <v-card-text>
          <v-layout justify-center>
            <v-flex xs4 text-center>
              <h4>Temperature</h4>
              <h1 class="display-1">{{ weather.name }}</h1>
              <img :src="icon" alt="Weather Icon" />
              <p>
                <span class="display-1">{{ temp() }} &deg;C</span>
                <span class="caption ml-4">{{ weather.weather[0].description }}</span>
              </p>
            </v-flex>
            <v-flex xs4 text-center>
              <h4>Wind & Pressure</h4>
              <h3 class="headline">Wind: {{ weather.wind.speed }} m/s ({{ weather.wind.deg }} &deg;)</h3>
              <h3 class="headline mt-4">Humidity: {{ weather.main.humidity }} %</h3>
              <h3 class="headline mt-4">Pressure: {{ weather.main.pressure }} hPa</h3>
            </v-flex>
            <v-flex xs4 text-center>
              <h4>Other: </h4>
              <h3 class="headline mt-4">Max Temperature: {{ Math.round(weather.main.temp_max - 273) }} &deg;C</h3>
              <h3 class="headline mt-4">Min Temperature: {{ Math.round(weather.main.temp_min - 273) }} &deg;C</h3>
            </v-flex>
          </v-layout>
        </v-card-text>
      </v-card>
    </v-flex>
    <v-flex xs12>
        <v-form @submit.prevent="getWeatherInfo()">
          <v-col
            cols="12"
            sm="12"
            md="12"
          >
            <v-text-field
              v-model="city"
              label="Enter City Name"
              solo
            ></v-text-field>
          </v-col>
        </v-form>
    </v-flex>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      city: 'London'
    }
  },
  asyncData({ $axios }) {
    return $axios.$get(`https://api.openweathermap.org/data/2.5/weather?q=London&appid=${process.env.WeatherAppId}`)
    .then(res => {
      return {
        weather: res
      }
    })
  },
  computed: {
    icon() {
      return this.weather.weather ? `https://openweathermap.org/img/w/${this.weather.weather[0].icon}.png` : ''
    }
  },
  methods: {
    getWeatherInfo() {
      return this.$axios.$get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${process.env.WeatherAppId}`)
      .then(res => (this.weather = res))
    },
    temp() {
      return Math.round(this.weather.main.temp) - 273
    }
  }
}
</script>

<style>

</style>