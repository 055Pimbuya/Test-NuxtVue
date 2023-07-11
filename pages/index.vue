<template>
  <div class="app-container">
    <div class="text-frame">
      <p>{{ message }}</p>
    </div>
    <div>
      <h2>
      <center>
      <fieldset>
       <legend> Test NuxtVue</legend>
        <br>
        <label> Input Number</label>
        <input type="" v-model="rows">
        <button @click="submit" style="background-color:#66CCFF; color:black; border-radius: 4px; font-size: 1rem;" >submit</button>
        <br>

        <ul v-if="showPyramids">
         <p><label>Show Daimond</label></p>
          <div class="pyramid-container">
            <ul v-for="(row, index) in pyramid" :key="index">
              <span v-for="num in row" :key="num" class="asterisk">*</span>
            </ul>
          </div>
          <div class="pyramid-container">

            <ul v-for="(row, index) in reversedPyramid" :key="index">
              <span v-for="(num, numIndex) in row" :key="numIndex" class="asterisk">
                {{ num }}
              </span>
            </ul>
          </div>
        </ul>
         </fieldset>
      </center>
      <div v-if="pyramid.length === 0"></div>
    </h2>
    </div>
  </div>
</template>

<style>
.pyramid-container {
  margin-bottom: 1px;
}

h2 {
  margin-bottom: 1px;
}

.asterisk {
  margin-right: 0px;
}
</style>

<script>
export default {
  data() {
    return {
      rows: 0,
      pyramid: [],
      reversedPyramid: [],
      showPyramids: false,
    };
  },
  methods: {
    generatePyramids() {
      const rows = parseInt(this.rows);
      if (!isNaN(rows) && rows > 0) {
        let pyramid = [];
        let reversedPyramid = [];
        let prev = "";
        let curr = "*";

        for (let i = 0; i < rows; i++) {
          let row = [];
          let reversedRow = [];
          for (let j = 0; j <= i; j++) {
            row.push(curr);
            reversedRow.unshift(curr);
            let temp = curr;
            curr = temp;
            prev = temp;
          }
          pyramid.push(row);
          reversedPyramid.push(reversedRow);
        }

        this.pyramid = pyramid;
        this.reversedPyramid = reversedPyramid.reverse();
      } else {
        this.pyramid = [];
        this.reversedPyramid = [];
      }
    },
    submit() {
      this.generatePyramids();
      this.showPyramids = true;
    },
  },
};
</script>
