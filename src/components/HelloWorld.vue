<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
      <div class="main-box">
        <div class="color" v-for="color in colorsOption" :key="color.value" >
          <div class="table-head">
            <p class="clor-name">{{ color.value }}</p>
            <div class="dropdown-icon"  @click="displaySizes(color)">
              <svg class="icon-drop" width="18" height="10" viewBox="0 0 18 10" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M1 1L9 9L17 1" stroke="#1A1A1A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </div>
          </div>
          <div v-if="selectedColor" class="table-details">
          <div v-for="(size, index) in selectedSizes" :key="index">
            {{ selectedColor.value }} - {{ size.name }}
          </div>
        </div>
        </div>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    msg: String
  },
  data() {
    return {
      colorsOption: [
        { value: "Blue", colorValue: "#ACCEEA" },
        { value: "Black", colorValue: "#252525" },
        { value: "Caribbean", colorValue: "#169AC1" },
        { value: "Charcoal", colorValue: "#4A4A4A" },
        { value: "Pink", colorValue: "#DE99B8" },
        { value: "Dark Heather", colorValue: "#3B3B3B" },
        { value: "Graphite Heather", colorValue: "#7E7C7D" },
        { value: "Heather Blue", colorValue: "#575A7D" },
        { value: "Heather Green", colorValue: "#3E7A53" },
        { value: "Heather Grey", colorValue: "#AFB0B2" },
      ],
      sizeOption: [
        { name: "XXL", value: "XXL" },
        { name: "XL", value: "XL" },
        { name: "L", value: "L" },
        { name: "M", value: "M" },
        { name: "S", value: "S" },
      ],
      selectedColor: null,
      selectedSizes: []
    };
  },
  computed: {
    variantList() {
      return this.selectedSizes.map(size => `${this.selectedColor.value} - ${size.name}`);
    }
  },
  methods: {
    displaySizes(color) {
      this.selectedColor = color;
      this.selectedSizes = this.sizeOption.slice(); // copy the size options array
      console.log('this.selectedSize :>> ', this.selectedSizes);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
  .table-head {
    display: flex;
    align-items: center;
    justify-content: center;
    grid-gap: 20px;
    margin-bottom: 20px;
  }
  .main-box {
    max-width: 550px;
    margin: 0 auto;
  }
  .icon-drop {
    width: 10px;
    height: 10px;
  }
  .clor-name {
    margin: 0;
  }
  .table-details {
    margin-bottom: 20px;
  }
</style>
