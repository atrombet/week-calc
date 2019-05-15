<template>
  <div id="app">
    <v-app dark>
      <v-container class="text-xs-center">
        <v-layout column justify-center align-center>
          <v-flex xs12>
            <h1 class="raleway">Week Calculator</h1>
            <h4 class="text-regular">By 
              <a href="http://kairostech.co" target="_blank">
                <span class="raleway text-bold">KAIROS</span>
                <span class="raleway text-thin">TECH</span>
              </a>
            </h4>
            <p class="mt-5">Ever wonder how many weeks are in a year?</p>
            <p>Now you don't have to.</p>
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex xs6 md2 offset-xs3 offset-md5>
            <v-select :items="years" labal="Choose a year" color="pink" @change="reset"></v-select>
          </v-flex>
        </v-layout>
        <v-layout column justify-center align-center class="ma-4">
          <v-btn color="pink" @click="calcWeeks">Calculate Weeks</v-btn>
        </v-layout>
        <v-layout v-if="weeks" column justify-center align-center>
          <h1 class="ma-3">{{weeks}}</h1>
          <v-btn flat @click="reset">Reset</v-btn>
        </v-layout>
      </v-container>
    </v-app>
  </div>
</template>

<script>

export default {
  name: 'app',
  data () {
    return {
      weeks: 0
    }
  },
  computed: {
    years: () => {
      let years = [];
      for (let year = 1990; year <= 2041; year++) {
        years.push(year);
      }
      return years;
    }
  },
  methods: {
    calcWeeks: function () {
      this.weeks = 52;
    },
    reset: function () {
      this.weeks = 0;
    }
  }
}
</script>

<style lang="scss">
@import '~rfs/scss';

h1 {
  @include font-size(4rem);
}

h4 {
  @include font-size(2rem);
}

p {
  @include font-size(2rem);
}

a {
  color: white;

  &:-webkit-any-link {
    color: white;
    cursor: pointer;
    text-decoration: none;
  }
}

.text-bold {
  font-weight: 600;
}

.text-regular {
  font-weight: 400;
}

.text-thin {
  font-weight: 200;
}

.raleway {
  font-family: 'Raleway', 'Roboto', sans-serif;
}
</style>
