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
    font-size: 1.8rem;
  }
      .body-style2{
    font-size: 0.8rem;
  }
    .body-style3{
    font-size: 0.5rem;
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
    <div class="text-block">
        <div class="body-style2">
            <p>Works Cited:</p>
        </div>
        <div class="body-style3">
            <p>Images:</p>
            <p>Reardon, Marguerite. The Broadband Gap’s Dirty Secret: Redlining Still Exists in Digital Form. CNET, 7 Oct. 2021, https://www.cnet.com/home/internet/features/the-broadband-gaps-dirty-secret-redlining-still-exists-in-digital-form/.,  “North St. Louis: A Gentrification-Free Zone.” What Beautiful Light, 19 June 2016, https://whatbeautifullight.com/2016/06/19/north-st-louis-a-gentrification-free-zone/.,  Redlining Map of St. Louis. Library of Congress, https://tile.loc.gov/storage-services/service/pnp/ppem/00700/00711v.jpg.,  Facebook Image: St. Louis Housing. Facebook, uploaded by user, https://scontent-dfw5-1.xx.fbcdn.net/v/t39.30808-6/521488198_598592793316646_7059045954250529162_n.jpg.,  Aerial View of St. Louis, Missouri. Cloudfront, https://d38zjy0x98992m.cloudfront.net/75303298-c86c-4a58-bf62-7a507776636e/2106130247_X_ST._LOUIS_MISSOURI_xgaplus.jpg.,  President Lyndon B. Johnson Signing Fair Housing Act. Fair Housing NJ, https://fairhousingnj.org/wp-content/uploads/2019/07/LBJ-signing-2-768x521-1.jpg.</p>
            <p>Websites:</p>
            <p>“Demographics and Disparities.” Think Health St. Louis, https://www.thinkhealthstl.org/demographicdata?id=1649&sectionId=940., “Home Loan Denial Rate.” City of St. Louis, https://www.stlouis-mo.gov/archives/resilience/equity/opportunity/financial-empowerment/home-loan-denial-rate.cfm., “Home Inequity: Race, Wealth, and Housing in St. Louis since 1940.”, Black Wealth Data Center, https://blackwealthdata.org/resources/library/Home-inequity%3A-race%2C-wealth%2C-and-housing-in-St.-Louis-since-1940.</p>
        </div>
    </div>


  <div class="chart-container">
    <Chart bind:chart {options} highcharts={Highcharts} />
  </div>
</div>
</div>

