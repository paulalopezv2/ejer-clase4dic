
# 🎧  "El Reproductor de Música Caótico"

#### Tiempo 
    60 Minutos 
#### Objetivo
 Transformar un código CSS monolítico, lleno de IDs y malas prácticas, en una arquitectura escalable aplicando SMACSS (para la organización), BEM (para los componentes) y OOCSS (para la reutilización).

## 1. El Escenario (El Código "Malo")
Eres contratado por "Spoti-Fake", una nueva app de música. El desarrollador anterior dejó este código. Funciona visualmente, pero es una pesadilla de mantener: usa IDs, estilos en línea y selectores súper específicos.

Tu Misión: Refactorizar este desastre sin romper el diseño visual.

##### CÓDIGO INICIAL (Copia esto en tu editor)

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<style>
  /* --- CÓDIGO A REFACTORIZAR --- */
  body { font-family: sans-serif; background: #333; margin: 0; }
  
  /* Layout mezclado con módulo */
  #music-wrapper { width: 400px; margin: 50px auto; background: #222; padding: 20px; border-radius: 10px; color: white; text-align: center; }
  
  /* Selectores anidados peligrosos */
  #music-wrapper div img { width: 100%; border-radius: 10px; margin-bottom: 20px; }
  
  #music-wrapper h2 { margin: 0; color: #1db954; font-size: 24px; }
  #music-wrapper p { color: #aaa; margin: 5px 0 20px 0; }
  
  /* Botones con estilos repetidos */
  .btn-play { background: #1db954; border: none; padding: 15px 30px; border-radius: 50px; color: white; font-size: 18px; cursor: pointer; }
  .btn-prev { background: #444; border: none; padding: 10px 20px; border-radius: 50px; color: white; cursor: pointer; margin-right: 10px; }
  .btn-next { background: #444; border: none; padding: 10px 20px; border-radius: 50px; color: white; cursor: pointer; margin-left: 10px; }
  
  /* Estilo dependiente del ID */
  #music-wrapper .progress-bar { width: 100%; height: 5px; background: #555; margin-bottom: 20px; position: relative; }
  #music-wrapper .progress-fill { width: 40%; height: 100%; background: #1db954; }

  /* Estado mezclado */
  .playing-now { border: 2px solid #1db954; }
</style>
</head>
<body>

  <div id="music-wrapper" class="playing-now">
    <div>
      <img src="https://via.placeholder.com/300" alt="Album Art">
    </div>
    <h2>Bohemian Rhapsody</h2>
    <p>Queen - A Night at the Opera</p>
    
    <div class="progress-bar">
      <div class="progress-fill"></div>
    </div>

    <div>
      <button class="btn-prev">⏮</button>
      <button class="btn-play">▶ Play</button>
      <button class="btn-next">⏭</button>
    </div>
  </div>

</body>
</html>
```

## 2. Instrucciones Paso a Paso (La Misión)
### FASE 1: Organización SMACSS (10 min)
En tu nuevo CSS, crea comentarios para separar las 5 categorías:

BASE: Mueve los estilos del body (fuente, reset de márgenes).

LAYOUT: Crea una clase .l-center que se encargue de centrar el reproductor en la pantalla. Pista: No uses IDs como #music-wrapper para el layout.

MODULE: Aquí irá el grueso del código (la tarjeta, los botones).

STATE: Para cuando la canción esté sonando.

THEME: Para colores personalizados.

### FASE 2: Componentes BEM (20 min)
Reescribe el HTML y CSS usando BEM para el reproductor.

Bloque Principal: Crea la clase .player. (Reemplaza a #music-wrapper).

Elementos:

La imagen debe ser .player__art.

El título (h2) debe ser .player__title.

El artista (p) debe ser .player__artist.

La barra de progreso debe ser .player__progress y su relleno .player__progress-fill.

### FASE 3: Botones OOCSS (15 min)
Tienes botones repetidos (.btn-play, .btn-prev, .btn-next). Aplica OOCSS:

Crea una clase de Estructura llamada .btn-control (padding base, bordes redondeados, cursor, sin borde).

Crea clases de Piel (Skin):

.skin-primary: Fondo verde, texto blanco (para el Play).

.skin-secondary: Fondo gris oscuro (para Prev/Next).

Actualiza el HTML para combinar clases: class="btn-control skin-secondary".

### FASE 4: Personalización Creativa - ¡Tu toque personal!
Crea una clase en la categoría THEME llamada .theme-retro (o el nombre que quieras).

Cuando esa clase esté en el body, el reproductor debe cambiar totalmente de colores (ej: fondo amarillo, letras negras, sombras duras).

Agrega un estado .is-paused en la categoría STATE que baje la opacidad de la portada del álbum.


 NO LO CLONE
 descarguelo para que pueda subirlo a su cuenta de github,

<image src="https://lh3.googleusercontent.com/rd-d/ALs6j_HrBy5ZxwZOIWAmBbxHeqZLVd-Dsg9dcDGoo2sbk3SbafqO-7mbTm1qlU1bUE__jOjTDdBmpSx9QtNgpG9pRlL0dr-z59shbM1jc8XstvHf0Hu2nlezT4t8rMM5L1XfQUWNiNV7Qftahs2Paw2jD9vpcgqG3dEZpW7jROMD3fizDvxdO827nOKWqv2-JVx92hwfICZoqaiK30Lw1JLQfQFG5OI8g0IjcDCwIIfUBz83gp9QKV9rXr4lkukEFfxN8wqmy3fPQIIXj6qyn0K0UoC0hlWiEAFmJTY6ogxNc-Kf-euuYZUSJGu_5Qs_6TuiDnTxAPL7fz6_2iqdhhrtGnmqYM4QRQ20qKpNqJlh0Qv1atFXmCUb8zibI2D7vxpjo7wal6VVVzxNScudV_aOkC6X2xrXNKkkLtgUN8lKkxq1fH4e-HwyGLUk5RsTtY7wZaXu9KDvTSxhsZvM3gZwIzR1QAi-7N9IYmZ4AldWi8bjoTpPssZdmPpnGb8-Jjjj69FbBjtH0VRT43hJejlZHtlaUAdAm2Ne_1TT0uFBEjjZY4_JEm9iY7U3b6aXBwoNw4RzCOctAUU-7-sK-_xRTLA23cHF8is5-cqIwQvqs9lIDSQRxla7mom90aP3ZvI-pp7KRiH-RaApiArdkTU3_iRvek_dKQgSXgeOtxTSWcyw7dOjG6Go56N87mqm5TOZ_EaRwG9PKBa04OAOhRSvmKCcLfbuwaF_HPDfVr8ldbvV7TFFRBExNH8IbE5MHQpl-Y9wM8ksIr5l__9wONHX8MqhLlypGm18LP25n5imYrk57Jz6l00kD1gBNASR5ptFHtL3Qf9xYHsX-TaTf7FSkgKTumDiZ2f4Cq4C8t6xW0O3TSzXuQ-KwOdt-P9GYzoRkfgWQDgI3PGF_7XxhqzB6Ar_PZY-o9Ie2m1Wg9GkBTGYE4pC3k0e94Nj9xqoIIVThajm25jvwlob_jV95nZTyO2t7usArxRGANhhJEVRuFJC0xU1ERn2HpZoA0mPZGI1dOCcSS5Dgg=w1920-h958?auditContext=prefetch" 
alt="Descripción de la imagen">

Abra los descargado con su visual studio code

Luego inicie su Repo 

```shell
git init
````
luego agregue sus cambios con estos comandos

```shell
git add . 
````

```shell
git commit -m "<comentario suyo>" 
````

```shell
git push 
````

Habilite el github pages , puede habilitar su rama main tal como aparece en la imagen.

<image src="https://lh3.googleusercontent.com/rd-d/ALs6j_GuXS-YAaeKCAgCLjQvAGVk61qT3UgztITCcUwMslPX8eGrqNB2qRM4Cueb5Ni9KaY91rGXC8HRaOmeC--lqqUQNLjnnEjBWJWlcOxgmdjX8E8sOQQSI9cLw8MH4-nIEHstHGVxUOov9BFLP4LAwBDPPpkNliWQDiPtwOqnWbNVGFB4AtmWAWGtuxEbPNe8VJZBZ041HRTo2kn-6oMcqrCS5XCLs4WDLzVI3GrqVlqKhn49kMR3z74wVcmQAb2_qRECjIU0k_TYdSR9B3PKmbte1vGYvtnMKqVyBmMbsvaNQOPbiqgzlbSBa4YSy16-aAzRHywOypbcTyq9exby6pz8gL3BAuUaOcnfv2ck1FdYrelUQH7TAyq531-IArWMCs8E7BMk8o0eRum-Rv8VlpMcNWDOmE10TUm8Bi9DbbbvuMqP2Qd619h3aUzyajIfVE3VdERh9tYpIzJwxHVrr_UQyv7yDywEqLpXXRh_Jy6qJamyjBOfgn8rodXu-kX2EpXi2E15D_qMAPmYFlpFpTRdmJbfkGJkEss9kXnL0IY9IEmUf649oAgyCNZ_lI6BhoRbiHS5ocbmy4yzZVQTbldjnwpKgadccfsjDzbtWZrNK_XuYKekm2kDTqDvKII3plbvCB3PfvLG389x_z8X-sNFijrNBr55PpuAbGAF5XGhSBjRkwVxLc5t_OL_EqZ0wackUpZYkKZfaKE_SAu7rWz-bq2GcMXSmPpoOu0_PWxNnyX3f-EzblOV6UbPQA3YOnJBIRRkK6QxDCJ-omfYGOzx3pG4hb9XENrJcFuL8g97tehRsIXGQHbJ594tESo5HCilMaf1ykwYRStsrIjtTjbjI3xxytevlaXvE-J3KU9RiQmPOMnHWGzskthT1bVaF2vyp5z0WI47lnreTVu2nTSFaCmflJUQlM9e8tuDEYbaWJMZeRENGRPpVtA4ahr-cm64IxD8qmwuaqcsrqwHFebxzojIX0qsm-mgNc0NObKAXoJIZeniino4W3FwRFbUnfppP-SeFw=w1920-h422?auditContext=prefetch" 
alt="Descripción de la imagen">