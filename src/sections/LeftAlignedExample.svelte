<script>
   import * as Highcharts from "highcharts";
   import "highcharts/modules/exporting";
   import { Chart } from "@highcharts/svelte";
   const series = [
     {
         name: "White Americans",
         data: [
             [1989, 130100],
             [2013, 134000],
             [2016, 163000],
             [2022, 287000],
         ],
         color: "white",
     },
     {
         name: "Black Americans",
         data: [
             [1989, 7700],
             [2013, 11200],
             [2016, 16000],
             [2022, 45000],
         ],
         color: "darkred",
     }
   ];

   let chart;

   let options = {
     chart: {
         type: "spline",
         backgroundColor: "ffffff", 
         borderColor: "#ffffff",
         borderWidth: 1,
     },
     title: {
         text: "White vs. Black Wealth in St. Louis",
         style: {
             color: "white"
         }
     },
     xAxis: {
         labels: { style: { color: "white" } },
         lineColor: "white",
         tickColor: "white"
     },
     yAxis: {
         labels: { style: { color: "white" } },
         title: { style: { color: "white" } },
         gridLineColor: "gray"
     },
     legend: {
         itemStyle: {
             color: "white"
         }
     },
     series: series
   };
</script>

<style>
  .scroller-section {
    display: flex;
    min-height: 300vh; 
    background-color: black; 
  }

  .chart-container {
    position: sticky;
    top: 0;
    height: 100vh;
    width: 57vw;
    overflow: hidden;
    background-image: url("https://tile.loc.gov/storage-services/service/pnp/ppem/00700/00711v.jpg");
    background-size: cover;
    background-position: center;

    padding-bottom: 0.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .text-content {
    width: 50vw;
    padding: 4rem 2rem;
    background: #090909;
  }

  .text-block {
    margin-bottom: 50vh;
    box-sizing: border-box;
    font-family: 'Playfair Display', serif;
    color: white;
  }

  .header-style {
    font-size: 2rem;
  }

  .body-style {
    font-size: 1.3rem;
  }
  
</style>

<div class="scroller-section">
  <div class="text-content">
    <div class="text-block">
      <div class="header-style">
        <h2>The Average Income: $73,913 for white households vs. $38,795 for Black households</h2>
      </div>
      <div class="body-style">
        <p>The average income for black households in the city of St. Louis is almost doubled by white households according to St.Louis-MO reaseachers.</p>
      </div>
    </div>
    <div class="text-block">
      <div class="header-style">
      <h2>Median home value: For Black people in the St. Louis city area home value has dropped by over $39,000, from 1940 to 2016</h2>
      </div>
       <div class="body-style">
      <p>According to an aricle on the BWDC website, the progressive home value decline dates all the way back to segregation in the 1940s. </p>
      </div>
    </div>
  </div>

  <div class="chart-container">
    <Chart bind:chart {options} highcharts={Highcharts} />
  </div>
</div>

