<script setup>
import { useRouter } from 'vue-router'

const router = useRouter();
const props = defineProps({
  entreprise: Object
});

const goToPage = (entreprise)=>{
  localStorage.setItem('Idticker', entreprise.ticker); // Stocker l'ID de l'utilisateur

  // Recharge la page après que les données ont été chargées avec succès
  router.push({ name: 'companie' }); // Redirection après la connexion

}
   

</script>

<template>

  <ul>
    <div class="card"  @click="goToPage(entreprise)">
      <img :src="entreprise.logo" alt="logo">
      <div class="card__content">
        <p class="card__title">{{ entreprise.name }}</p>
        <p class="card__description"> {{ entreprise.ticker }}</p>
      </div>
    </div>
  </ul>
  

</template>


<style scoped>
ul {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center; /* Centrer les éléments verticalement si nécessaire */
  padding: 0; /* Enlever le padding par défaut des ul */
  list-style-type: none; /* Enlever les puces par défaut */
  width: 100%; /* Prendre toute la largeur si nécessaire */
}

.card {
  position: relative;
  width: 500px;
  height: 200px;
  background-color: #f2f2f2;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  perspective: 1000px;
  box-shadow: 0 0 0 5px #ffffff80;
  transition: all 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  margin-top: 20px;
}

.card img {
  width: 48px;
  fill: #333;
  transition: all 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.card:hover {
  transform: scale(1.05);
  box-shadow: 0 8px 16px rgba(255, 255, 255, 0.2);
}

.card__content {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  padding: 20px;
  box-sizing: border-box;
  background-color: #f2f2f2;
  transform: rotateX(-90deg);
  transform-origin: bottom;
  transition: all 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.card:hover .card__content {
  transform: rotateX(0deg);
}

.card__title {
  margin: 0;
  font-size: 24px;
  color: #333;
  font-weight: 700;
}

.card:hover img {
  scale: 0;
}

.card__description {
  margin: 10px 0 0;
  font-size: 14px;
  color: #777;
  line-height: 1.4;
}

</style>