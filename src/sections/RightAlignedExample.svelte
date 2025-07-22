<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    const series = [
    {
      name: "Group",
      data: [
        { name: "Black people rejected", y: 23.9, color:"#7992a2" },
        { name: "Black people accepted", y: 76.1, color:"#5c7485" },
        { name: "White people accepted", y: 93.8, color:"#790d0d" },
        { name: "White people rejected", y: 6.2, color:"#B12020" },
        
      ],
    },
  ];

  let chart;

  let options = {
    chart: {
      type: "pie",
      backgroundColor: "transparent",
    },
    title: {
      text: "Home Loan Denial Rates",
      style: { color: "white" },
    },
    plotOptions: {
      pie: {
        allowPointSelect: true,
        dataLabels: {
          enabled: true,
          distance: 20,
          format: "{point.percentage:.1f}%",
          style: {
            fontSize: "1.2em",
            color: "white",
            textOutline: "none",
          },
          filter: {
            operator: ">",
            property: "percentage",
            value: 10,
          },
        },
      },
    },
    series: series,
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
    background-image: url("https://d38zjy0x98992m.cloudfront.net/75303298-c86c-4a58-bf62-7a507776636e/2106130247_X_ST._LOUIS_MISSOURI_xgaplus.jpg");
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
    margin-bottom: 20vh;
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
  .image-block{
  object-fit: cover;
  width: 100%;
  height: 80vh; 
  overflow: hidden;
  border-radius: 20px;
  }
</style>

<div class="scroller-section">
    <div class="chart-container">
    <Chart bind:chart={chart} {options} highcharts={Highcharts} />
  </div>
  <div class="text-content">
    <div class="text-block">
      <div class="header-style">
        <h2>In STL city, 23.9% of Black applicants get declined a loan compared to only 6.2% of white applicants</h2>
      </div>
      <div class="body-style">
        <p>The chart to the left represnts 100 applicants total, 50 being black and 50 being white. This data illuminates the economic stress some have to deal with in the St. Louis community and show the racial differences in borrowing, income, and financial opportunity.</p>
      </div>
    </div>
    <div class="image-block">
        <img src="https://www.stlouisfed.org/-/media/project/frbstl/stlouisfed/images/about-us/history/stlouisfed_1924.jpg">
    </div> 
    <div class="text-block">
        <div class="header-style">
      <h2>Generational Wealth: Easy access to make economic investmnets, made it easy for white households wealth to prosper.</h2>
      </div>
        <div class="body-style">
      <p>Finnacial stability and the ability for white Americans to get loans to start businesses provided wealth for their households childen, grand-childen, and generations to come.</p>
      </div>
    </div> 
    </div>
</div>