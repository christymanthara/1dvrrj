<script>
  import { scaleLinear } from 'd3-scale'
  import { data } from './data.js'
let barXPosition = 100
 let yPosition = 100
 const widthScale = scaleLinear()
                    .domain([0, 500])
                    .range([0, 400])


 function yPos (index, height) {
console.log(index,height)
   if(height>=15){
    return (index+height/2);
   }
    else
    {
    return index;
  }}


  function respondToClick(i)
  {
    console.log('i have been clicked' + (i+1));
    i.style.fill = "black";
  }
</script>


<div class="graph">
  <div class="title">
    <!-- title/header content goes here -->
    <h1>Occupations in which American Negroes are engaged</h1>
        <h2>Occupations et industries des Negres Americains</h2>
        <h3>Done by Atlanta University</h3>
  </div>
  <div class="main-chart">
    <!-- main chart -->
      <!-- {#each data as item,i}
     <h1>{item.jobPixelsAgri}</h1>
     <h1>{item.jobColorAgri}</h1>
     {/each} -->
    <svg id="chart" width="900" height="600">
     {#each data as item,i}
     <text class = "textStyle1"  x={item.xValue} y={item.yValue} dy={10}>{item.title}</text> 
     <text class = "textStyle1"  x={item.xValue} y={item.yValue+20} dy={10}>{item.frenchTitle}</text> 
     <rect on:click={() => respondToClick(i)} class="bar" x={200*i+50} y={yPosition} height={widthScale(item.jobPixelsAgri)} fill={item.jobColorAgri} width="100" />
     <rect on:click={() => respondToClick(i)} class="bar" x={200*i+50} y={item.jobPixelsAgri+yPosition} height={item.jobPixelsProf} fill={item.jobColorProf} width="100" />
     <rect on:click={() => respondToClick(i)} class="bar" x={200*i+50} y={item.jobPixelsProf+yPosition+item.jobPixelsAgri} height={item.jobPixelsDomestic} fill={item.jobColorDomestic} width="100" />
     <rect on:click={() => respondToClick(i)} class="bar" x={200*i+50} y={item.jobPixelsProf+yPosition+item.jobPixelsAgri+item.jobPixelsDomestic} height={item.jobPixelsCommerce} fill={item.jobColorCommerce} width="100" />
     <rect on:click={() => respondToClick(i)} class="bar" x={200*i+50} y={item.jobPixelsProf+yPosition+item.jobPixelsAgri+item.jobPixelsDomestic+item.jobPixelsCommerce} height={item.jobPixelsMech} fill={item.jobColorMech} width="100" />


     <text class = "textStyle2" x ={200*i+50} y={yPos(0,item.jobPixelsAgri)} dy={10}>{item.jobTypeAgri}</text>
     
    <text class = "textStyle2" x ={200*i+50} y={yPos(item.jobPixelsAgri+yPosition,item.jobPixelsProf)} dy={10}>{item.jobTypeProf}</text>
    <text class = "textStyle2" x ={200*i+50} y={yPos(item.jobPixelsAgri+yPosition+item.jobPixelsProf,item.jobPixelsDomestic)} dy={10}>{item.jobTypeDomestic}</text>
    <text class = "textStyle2" x ={200*i+50} y={yPos(item.jobPixelsAgri+yPosition+item.jobPixelsProf+item.jobPixelsDomestic,item.jobPixelsCommerce)} dy={10}>{item.jobTypeCommerce}</text>
    <text class = "textStyle2" x ={200*i+50} y={yPos(item.jobPixelsAgri+yPosition+item.jobPixelsProf+item.jobPixelsDomestic+item.jobPixelsCommerce,item.jobPixelsMech)} dy={10}>{item.jobTypeMech}</text>

     {/each}
    </svg>
  </div>
</div>

<style>
.graph {
  width: 600px;
  background-color: rgb(250, 239, 233);
  padding: 10px;
}

/* styles go here */

h1,
h2,
h3 {
  text-align: Center;
  color: grey;
  font-weight: 200;
}
rect {
  stroke: rgb(50, 50, 50);
}

@font-face {
  src: url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital@1&display=swap');
  font-family: 'Playfair Display', serif;
}

#headerBars {
  font-family: 'Oswald', sans-serif;
}

#subHeaderBars {
  font-family: 'Oswald', sans-serif;
  font-size: x-small;
  font-weight: 200;
}

body {
  margin: 0;
  /* width: 600px; */
  background-color: rgb(250, 239, 233);
  line-height: 1.5;
  font-family: 'Open Sans', 'PT Sans', Calibri, Tahoma, sans-serif;
}

@font-face {
  src: url('https://fonts.googleapis.com/css2?family=Oswald&family=Playfair+Display:ital@1&display=swap');
  font-family: 'Oswald', sans-serif;
  /* font-family: 'Playfair Display', serif; */
}

.allContents {
  padding: 80px;
}

.title {
  src: url('https://fonts.googleapis.com/css2?family=Noto+Serif+Vithkuqi&family=Oswald:wght@200;400&family=Playfair+Display:ital@1&display=swap');
  font-family: 'Noto Serif Vithkuqi', serif;
}

.textStyle1{
  font-size:smaller;
  dominant-baseline:hanging;
  text-anchor : middle;
}

.textStyle2{
  font-size:10px;
  dominant-baseline:hangling;
  width: fit-content;
}
.container{
  padding: 10px;
  width: 20em;
  transition: fill 0.3s ease;
}

.container:hover {
    fill: red; /* Change this to the desired color */
  }

  .bar:hover .bar-rect {
  fill: red; /* Change this to the desired hover color */
}


</style>