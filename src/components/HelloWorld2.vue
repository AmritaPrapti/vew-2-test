<template>
  <div>
    <ul class="colorSize-list">
      <li class="color-list-item" v-for="color in colorWithOptions" :key="color.value">
        <div class="clor-list-wrap">
            <p class="color-name">{{ color.value }} <span >{{ color.sizeOptions.length }} </span></p> 
            <div @click="selectColor(color)">
                <svg class="drop-down" width="18" height="10" viewBox="0 0 18 10" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M1 1L9 9L17 1" stroke="#1A1A1A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
            </div>
        </div>
        <ul class="sizeList" v-if="selectedColor === color">
          <li class="size-list-item" v-for="size in color.sizeOptions" :key="size.value">
            {{ size.name }}
          </li>
        </ul>
      </li>
    </ul>
  </div>
</template>
  
  <script>
export default {
  data() {
    return {
      colorWithOptions: [],
      selectedColor: null,
    };
  },
  methods: {
    createColorWithOptions() {
      this.colorWithOptions = this.colorsOption.map((color) => {
        const colorElement = { ...color };
        colorElement.sizeOptions = this.sizeOption.map((size) => ({ ...size }));
        return colorElement;
      });
      console.log('colorWithOptions :>> ', this.colorWithOptions);
    },
    selectColor(color) {
      this.selectedColor = color === this.selectedColor ? null : color;
    },
   
  },
  computed: {
    colorsOption() {
      return [
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
      ];
    },
    sizeOption() {
      return [
        { name: "XXL", value: "XXL" },
        { name: "XL", value: "XL" },
        { name: "L", value: "L" },
        { name: "M", value: "M" },
        { name: "S", value: "S" },
      ];
    },
  },
  mounted() {
    this.createColorWithOptions();
  },
};
</script>

<style>
.colorSize-list , .sizeList{
    list-style: none;
}
.clor-list-wrap {
    display: flex;
    align-items: center;
    grid-gap: 10px;
}
.drop-down {
    width: 10px;
    height: 10px;
}
.sizeList{
    display: flex;
    flex-direction: column;
    align-items: baseline;
    padding-left: 10px;
}
</style>
  