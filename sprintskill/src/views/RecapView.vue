<script setup>
</script>

<template>
  <div class="recap">
    <div class="sommaire">

      <h2>Récapitulatif de votre frappe</h2>

      <div class="star-container">

        <span class="star">⭐</span>
        <span class="star">⭐</span>
        <span class="star">⭐</span>
        <span class="star">⭐</span>
        <span class="star">⭐</span>

      </div>

    </div>

    <div class="summary-container">

      <div class="circle">

        <div class="circle-content">

          <p><strong>50 MPM</strong></p>

        </div>

        <p>Vitesse</p>

      </div>

      <div class="circle duration-circle">

        <div class="circle-content">

          <p><strong>30 s</strong></p>

        </div>

        <p>Durée</p>

      </div>
      
    </div>
    <div class="btn">
      <button>Recommencer</button>
    </div>
  </div>

</template>

<style scoped>
/*************************************  Css REcapView **********************************************/

.star {
  font-size: 24px;
}

.star.yellow img {
  filter: brightness(1.5);
}

.star-container {
  display: flex;
  justify-content: center;
}

.recap {
  /* background-repeat: no-repeat;
  background-position: center;
  background-size: cover; */

  background-image: url("../assets/cl9.jpg");
  background: transparent;
  background-size: cover;
  backdrop-filter: blur(50px);


  width: 50%;
  margin: auto;

  /*********/
  background-color: #FFFFFF00;
  position: absolute;
  /* top: 0;
  left: 250px; */


  left: 50%;
  top: 40%;
  transform: translate(-50%, -50%);
}
 </style>

