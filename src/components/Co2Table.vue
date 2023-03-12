<template>
  <div id="co2table">
    <h1>CO2-Emissionsdaten</h1>
    <div class="filters">
      <div>
        <label for="country">Land:</label>
        <select id="country" v-model="selectedCountry">
          <option value="">Alle Länder</option>
          <option v-for="country in countries" :key="country">{{ country }}</option>
        </select>
      </div>
      <div>
        <label for="company">Unternehmen:</label>
        <select id="company" v-model="selectedCompany">
          <option value="">Alle Unternehmen</option>
          <option v-for="company in companies" :key="company">{{ company }}</option>
        </select>
      </div>
    </div>
    <table>
      <thead>
        <tr>
          <th @click="sortBy('country')">Land</th>
          <th @click="sortBy('company')">Unternehmen</th>
          <th @click="sortBy('co2')">CO2-Emissionen (kg)</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="data in sortedData" :key="data.id">
          <td>{{ data.country }}</td>
          <td>{{ data.company }}</td>
          <td>{{ data.co2 }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedCountry: '',
      selectedCompany: '',
      data: [
        { id: 1, country: 'Deutschland', company: 'Volkswagen', co2: 10000 },
        { id: 2, country: 'Deutschland', company: 'BMW', co2: 8000 },
        { id: 3, country: 'USA', company: 'Tesla', co2: 5000 },
        { id: 4, country: 'USA', company: 'Ford', co2: 12000 },
        { id: 5, country: 'China', company: 'BYD', co2: 4000 },
        { id: 6, country: 'China', company: 'Geely', co2: 7000 },
        { id: 7, country: 'Japan', company: 'Toyota', co2: 9000 },
        { id: 8, country: 'Japan', company: 'Honda', co2: 6000 },
        { id: 9, country: 'South Korea', company: 'Hyundai', co2: 8500 },
        { id: 10, country: 'South Korea', company: 'Kia', co2: 7500 },
        { id: 11, country: 'France', company: 'Renault', co2: 11000 },
        { id: 12, country: 'France', company: 'Peugeot', co2: 9500 },
        { id: 13, country: 'Italy', company: 'Ferrari', co2: 3000 },
        { id: 14, country: 'Italy', company: 'Fiat', co2: 10000 },
        { id: 15, country: 'Sweden', company: 'Volvo', co2: 8500 },
        { id: 16, country: 'Sweden', company: 'Saab', co2: 9500 },
        { id: 17, country: 'Netherlands', company: 'Tesla', co2: 5000 },
        { id: 18, country: 'Netherlands', company: 'TomTom', co2: 2000 },
        { id: 19, country: 'India', company: 'Tata Motors', co2: 6000 },
        { id: 20, country: 'India', company: 'Mahindra & Mahindra', co2: 5500 },
        { id: 21, country: 'Canada', company: 'Ford', co2: 12000 },
        { id: 22, country: 'Canada', company: 'Bombardier', co2: 3000 },
        { id: 23, country: 'Russia', company: 'Lada', co2: 9500 },
        { id: 24, country: 'Russia', company: 'GAZ', co2: 8000 },
        { id: 25, country: 'Spain', company: 'SEAT', co2: 7000 },
        { id: 26, country: 'Spain', company: 'Renault', co2: 11000 },
        { id: 27, country: 'Australia', company: 'Holden', co2: 9000 },
        { id: 28, country: 'Australia', company: 'Tesla', co2: 5000 },
        { id: 29, country: 'Brazil', company: 'Volkswagen', co2: 10000 },
      ],
      sortKey: '',
      sortOrder: 1,
    };
  },
  computed: {
    countries() {
      return Array.from(new Set(this.data.map(item => item.country)));
    },
    companies() {
      return Array.from(new Set(this.data.map(item => item.company)));
    },
    filteredData() {
      let filteredData = this.data;
      if (this.selectedCountry !== '') {
        filteredData = filteredData.filter(item => item.country === this.selectedCountry);
      }
      if (this.selectedCompany !== '') {
        filteredData = filteredData.filter(item => item.company === this.selectedCompany);
      }
      return filteredData;
    },
    sortedData() {
      let sortedData = this.filteredData;
      if (this.sortKey !== '') {
        sortedData = sortedData.sort((a, b) => {
          const valA = a[this.sortKey];
          const valB = b[this.sortKey];
          if (typeof valA === 'string' && typeof valB === 'string') {
            return this.sortOrder * valA.localeCompare(valB);
          } else {
            return this.sortOrder * (valA - valB);
          }
        });
      }
      return sortedData;
    },
  },
  methods: {
    sortBy(key) {
      if (this.sortKey === key) {
        this.sortOrder *= -1;
      } else {
        this.sortOrder = 1;
        this.sortKey = key;
      }
    },
  },
}
</script>


<style>
h1 {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 1rem;
}

#co2table {
  margin: 10px;
  width: 90%;
}

.filters div {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}

label {
  font-weight: bold;
  text-align: right;
  margin-right: 0.5rem;
  min-width: 7rem;
  /* Set a minimum width for the label */
}

select {
  padding: 0.5rem;
  font-size: .8rem;
  border: 1px solid gray;
  border-radius: 5px;
  margin: 0 auto;
  max-width: max-content;
  width: 100%;
  /* Set the select width to 100% to fill the container */
}


/* Responsive styles for table */
.table-container {
  max-width: 100%;
  overflow-x: auto;
}

table {
  width: 100%;
  border-collapse: collapse;
  border: 1px solid gray;
}

th {
  font-weight: bold;
  text-align: left;
  cursor: pointer;
  user-select: none;
  border: 1px solid gray;
}

td {
  border: 1px solid gray;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

/* Hover effect for mobile */
@media (hover: none) {
  tr:hover {
    background-color: #ddd;
  }
}
</style>
