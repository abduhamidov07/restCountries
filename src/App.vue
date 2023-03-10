<template>
  <div class="total">
    <h1 class="title">Send a request to the API</h1>
    <div class="sidebar">
      <div class="card">
        <div v-if="loading">Loading...</div>
        <div v-else-if="error">Error: {{ error }}</div>
        <div v-else>
          <div class="cardInfo">
            <h2>
              {{ countryUz.name }}
            </h2>
            <p>Continent: <span>{{ countryUz.region }}</span></p>
            <p>Country: <span>{{ countryUz.nativeName }}</span></p>
            <p>Capital: <span>{{ countryUz.capital }}</span></p>
            <p>Area: <span>{{ countryUz.area }} km<sup>2</sup></span></p>
            <p>Population: <span>{{ countryUz.population }}</span></p>
            <p>Time: <span>{{ countryUz.timezones[0] }}</span></p>
          </div>
        </div>
      </div>
      <div class="card">
        <div v-if="loading">Loading...</div>
        <div v-else-if="error">Error: {{ error }}</div>
        <div v-else>
          <div class="cardInfo">
            <h2>
              {{ countryCh.name }}
            </h2>
            <p>Continent: <span>{{ countryCh.region }}</span></p>
            <p>Country: <span>{{ countryCh.nativeName }}</span></p>
            <p>Capital: <span>{{ countryCh.capital }}</span></p>
            <p>Area: <span>{{ countryCh.area }} km<sup>2</sup></span></p>
            <p>Population: <span>{{ countryCh.population }}</span></p>
            <p>Time: <span>{{ countryCh.timezones[0] }}</span></p>
          </div>
        </div>
      </div>
      <div class="card">
        <div v-if="loading">Loading...</div>
        <div v-else-if="error">Error: {{ error }}</div>
        <div v-else>
          <div class="cardInfo">
            <h2>
              {{ countryRu.name }}
            </h2>
            <p>Continent: <span>{{ countryRu.region }}</span></p>
            <p>Country: <span>{{ countryRu.nativeName }}</span></p>
            <p>Capital: <span>{{ countryRu.capital }}</span></p>
            <p>Area: <span>{{ countryRu.area }} km<sup>2</sup></span></p>
            <p>Population: <span>{{ countryRu.population }}</span></p>
            <p>Time: <span>{{ countryRu.timezones[0] }}</span></p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loading: true,
      errror: null,
      countryUz: null,
      countryCh: null,
      countryRu: null,
    };
  },
  created() {
    fetch(`https://restcountries.com/v2/name/Uzbekistan`)
      .then((response) => response.json())
      .then((data) => {
        this.countryUz = data[0];
        this.loading = false;
      })
      .catch((error) => {
        console.log(error);
        this.error = "An error occurred";
        this.loading = false;
      });
    fetch("https://restcountries.com/v2/name/China")
      .then((response) => response.json())
      .then((data) => {
        this.countryCh = data[0];
        this.loading = false;
      })
      .catch((error) => {
        console.log(error);
        this.error = "An error occurred";
        this.loading = false;
      });
    fetch("https://restcountries.com/v2/name/Russia")
      .then((response) => response.json())
      .then((data) => {
        this.countryRu = data[0];
        this.loading = false;
      })
      .catch((error) => {
        console.log(error);
        this.error = "An error occurred";
        this.loading = false;
      });
  },
};
</script>

<style scoped></style>
