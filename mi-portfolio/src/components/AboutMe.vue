
<template>
<main class="container">
    <div class="logomain"></div>
    <div class="example">
        <!-- Flora -->
        <div class="flora">
            <div class="flora-content">
                <img src="../assets/nay.png" alt="Flora" class="flora-image">
                <p class="flora-text">  
                    <b>Flora:</b> The first fairy is an artist who primarily uses pencils and black liner to go over her illustrations.<br><br>
                    Although she has recently focused on graphic design work, she occasionally returns to the basics of pencil, eraser, and paper.  
                  </p>
            </div>
        </div>
        <!-- Fauna -->
        <div class="fauna">
            <div class="fauna-content">
                <img src="../assets/olatz.png" alt="Fauna" class="fauna-image">
                <p class="fauna-text">  
                    <b>Fauna:</b> The second fairy, on the other hand, specializes in colored illustrations using markers of all brands and types, both water-based and alcohol-based.<br><br>  
                    She pays great attention to the details of clothing, as she studied fashion design.<br><br>  
                    Her works are usually colorful and dynamic, closely resembling the Japanese manga style.  
                </p>
                
            </div>
        </div>
        <!-- Merryweather -->
        <div class="merryweather">
            <div class="merryweather-content">
                <img src="../assets/tania.png" alt="Merryweather" class="merryweather-image">
                <p class="merryweather-text">  
                    <b>Merryweather:</b> The third and final fairy of the group is a highly versatile artist. Lately, she has specialized in digital illustrations.<br><br>  
                    She is capable of replicating any coloring style and blending it with her own unique and original approach.<br><br>  
                    She is very detail-oriented and carefully refines every aspect of her illustrations <br> and enjoys conducting an in-depth study of light and how it would behave in the different scenes she draws.  
                </p>
            </div>
        </div>
    </div>
</main>
</template>


<style scoped>
/* Configuración general de cada fila */
.flora-content,
.fauna-content,
.merryweather-content {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 70%; 
  gap: 10rem;
}

/* Flora y Merryweather alineados con imagen a la izquierda */
.flora-content,
.merryweather-content {
  flex-direction: row; 
  margin-left: 20rem;
}

/* Fauna alineada con imagen a la derecha */
.fauna-content {
  flex-direction: row-reverse; 
  margin-left: 20rem;
}

/* Ajuste de imágenes */
.flora-image,
.fauna-image,
.merryweather-image {
  width: 600px;
  height: auto;
}

/* Ajuste de textos */
.flora-text,
.merryweather-text,
.fauna-text {
  text-align: left; 
  font-size: 1.5rem;
  max-width: 700px;
}

.flora-text b,
.fauna-text b,
.merryweather-text b {
  font-weight: bold;
}

.fauna-text {
  text-align: right; 
}
</style>