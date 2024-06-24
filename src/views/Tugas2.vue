<template>
    <q-page class="q-pa-md custom-page">
      <div class="custom-container">
        <div class="custom-card-wrapper">
          <q-card flat bordered class="custom-card">
            <q-card-section class="custom-card-section">
              <h2 class="custom-card-title">Tugas 2</h2>
              <p class="custom-card-description">Tidak Bikin.</p>
            </q-card-section>
          </q-card>
        </div>
      </div>
    </q-page>
  </template>
  
  <script>
  export default {
    name: 'App',
  };
  </script>
  
  <style scoped>
  .custom-page {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background: linear-gradient(45deg, #FF6347, #FFD700);
    padding: 0;
  }
  
  .custom-container {
    max-width: 800px;
    width: 100%;
    padding: 2rem;
  }
  
  .custom-card-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .custom-card {
    width: 100%;
    background-color: #1e1e1e;
    border: 3px solid #FFD700;
    border-radius: 20px;
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
    overflow: hidden;
    transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
  }
  
  .custom-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.4);
  }
  
  .custom-card-section {
    padding: 30px;
    text-align: center;
  }
  
  .custom-card-title {
    font-size: 2.5rem;
    font-weight: 700;
    color: #FFD700;
    margin-bottom: 1rem;
  }
  
  .custom-card-description {
    font-size: 1.3rem;
    color: #F0F0F0;
  }
  </style>
  