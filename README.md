# PregutasJR
Preguntas
.html  <!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="estilo.css">
    <title>ADIVINA LA BANDERA</title>
</head>
<body>
    <h1>ADIVINA LA BANDERA</h1>

    <!-- Pantalla inicial -->
    <div id="pantalla-inicial">
        <p>¿A qué pais pertenece la bandera?</p>
        <button class="btn" onclick="comenzarJuego()">COMENZAR A JUGAR</button>
    </div>

    <!-- Pantalla juego -->
    <div class="pantalla-juego" id="pantalla-juego">
        <img src="img/ad.svg" alt="" id="imgBandera">
        <div class="opciones">
            <div class="opcion" id="op0" onclick="comprobarRespuesta(0)">
                <div class="letra" id="l0">A</div>
                <div class="nombre" id="n0">OPCION A</div>
            </div>
            <div class="opcion" id="op1" onclick="comprobarRespuesta(1)">
                <div class="letra" id="l1">B</div>
                <div class="nombre" id="n1">OPCION B</div>
            </div>
            <div class="opcion" id="op2" onclick="comprobarRespuesta(2)">
                <div class="letra" id="l2">C</div>
                <div class="nombre" id="n2">OPCION C</div>
            </div>
            <div class="opcion" id="op3" onclick="comprobarRespuesta(3)">
                <div class="letra" id="l3">D</div>
                <div class="nombre" id="n3">OPCION D</div>
            </div>
        </div>
    </div>
    <!-- Pantalla final -->
    <div id="pantalla-final">
        <h2>CORRECTAS: <span id="numCorrectas">3</span></h2>
        <h2>INCORRECTAS: <span id="numIncorrectas">2</span></h2>
        <button class="btn" onclick="volverAlInicio()">VOLVER AL INICIO</button>
    </div>
    
    <script src="script.js"></script>
</body>
</html>




.css@import url('https://fonts.googleapis.com/css2?family=Mochiy+Pop+One&display=swap');
*{
    box-sizing: border-box;
    font-family: 'Mochiy Pop One';
}
body{
    background: url(img/fondo.jpg);
    background-size: cover;
    background-attachment: fixed;
    margin: 0;
}
h1{
    width: fit-content;
    background-color: #fff;
    margin: 40px auto;
    border-radius: 60px;
    box-shadow: 5px 5px 0 #000;
    padding: 20px 30px;
}
footer{
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    background-color: #000;
    color: #000;
    font-size: 12px;
    color: #fff;
    padding: 10px;
    text-align: center;
}

/* PANTALLA INICIO */
#pantalla-inicial{
    display: block;
    text-align: center;
    font-size: 30px;
}
#pantalla-inicial{
    margin: 60px 0;
}
.btn{
    border: none;
    background: #580078;
    color: #fff;
    padding: 10px 20px;
    border-radius: 50px;
    cursor: pointer;
    transition: .5s;
}
.btn:hover{
    transform: scale(1.1);
}



/* PANTALLA juego */
#pantalla-juego{
    display: none;
}
.pantalla-juego{
    max-width: 800px;
    margin: 50px auto;
    text-align: center;
}
.pantalla-juego img{
    max-width: 400px;
    width: 100%;
}
.opciones{
    max-width: 400px;
    margin: auto;
}
.opcion{
    display: flex;
    position: relative;
    align-items: center;
    max-width: 400px;
    margin: 30px auto;
    cursor: pointer;
}
.opcion .letra{
    background-color: #580078;
    width: 50px;
    height: 50px;
    font-size: 30px;
    font-weight: bold;
    color: #fff;
    text-align: center;
    border-radius: 50%;
    line-height: 35px;
    border: 5px solid #fff;
    position: relative;
}
.opcion .nombre{
    background: #fff;
    width: 100%;
    font-size: 25px;
    position: absolute;
    margin-left: 30px;
    z-index: -2;
    border-radius: 0 20px 20px 0;
    padding: 7px 0 7px 30px;
}
/* clases que se aplicará cuando haya acertada la opcion  */
.opcion .nombreAcertada{
    background-color: yellowgreen;
    color: #fff;
}
.opcion .letraAcertada{
    background-color: yellowgreen;
    color: #fff ;
}
/* clases que se aplicaran cuando se equivoque en la opcion elegida */
.opcion .nombreNoAcertada{
    background-color: darkred;
    color: #fff;
}
.opcion .letraNoAcertada{
    background-color: darkred;
    color: #fff;
}




/* PANTALLA final */
#pantalla-final{
    display: none;
    text-align: center;
}
#pantalla-final #numCorrectas{
    background-color: chartreuse;
    display: inline-block;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    border: 5px solid #fff;
}
#pantalla-final #numIncorrectas{
    background-color: darkred;
    display: inline-block;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    border: 5px solid #fff;
}








.js  //cargo en un arreglo las imganes de las banderas. Este sera el orden que se mostrarán
let banderas = ["pa.svg", "bo.svg", "ad.svg", "gb.svg", "na.svg","pa.svg", "bo.svg", "ad.svg", "gb.svg", "na.svg","pa.svg", "bo.svg", "ad.svg", "gb.svg", "na.svg","pa.svg", "bo.svg", "ad.svg", "gb.svg", "na.svg"];

//arreglo que guardara la opcion correcta
let correcta = [2,2,1,1,0,2,2,1,1,0,2,2,1,1,0,2,2,1,1,0];

//arreglo que guardara los paises a mostrar en cada jugada
let opciones = [];
//cargo en el arreglo opciones las opciones a mostrar en cada jugada
opciones.push(["Costos de Evaluación", "Costos Internos", "Costos Externos", "Costos De Falla"]);
opciones.push(["PERU", "ITALIA", "BOLIVIA"]);
opciones.push(["TUNEZ", "ANDORRA", "ANTIGUA Y BARBUDA"]);
opciones.push(["UCRANIA", "REINO UNIDO", "MADAGASCAR"]);
opciones.push(["NAMIBIA", "OMAN", "ETIOPIA"]);
opciones.push(["Costos de Evaluación", "Costos Internos", "Costos Externos", "Costos De Falla"]);
opciones.push(["PERU", "ITALIA", "BOLIVIA"]);
opciones.push(["TUNEZ", "ANDORRA", "ANTIGUA Y BARBUDA"]);
opciones.push(["UCRANIA", "REINO UNIDO", "MADAGASCAR"]);
opciones.push(["NAMIBIA", "OMAN", "ETIOPIA"]);
opciones.push(["Costos de Evaluación", "Costos Internos", "Costos Externos", "Costos De Falla"]);
opciones.push(["PERU", "ITALIA", "BOLIVIA"]);
opciones.push(["TUNEZ", "ANDORRA", "ANTIGUA Y BARBUDA"]);
opciones.push(["UCRANIA", "REINO UNIDO", "MADAGASCAR"]);
opciones.push(["NAMIBIA", "OMAN", "ETIOPIA"]);
opciones.push(["Costos de Evaluación", "Costos Internos", "Costos Externos", "Costos De Falla"]);
opciones.push(["PERU", "ITALIA", "BOLIVIA"]);
opciones.push(["TUNEZ", "ANDORRA", "ANTIGUA Y BARBUDA"]);
opciones.push(["UCRANIA", "REINO UNIDO", "MADAGASCAR"]);
opciones.push(["NAMIBIA", "OMAN", "ETIOPIA"]);

//variable que guarda la posicion actual
let posActual = 0;
//variable que guarda la cantidad acertadas hasta el moemento
let cantidadAcertadas = 0;

function comenzarJuego(){
    //reseteamos las variables
    posActual = 0;
    cantidadAcertadas = 0;
    //activamos las pantallas necesarias
    document.getElementById("pantalla-inicial").style.display = "none";
    document.getElementById("pantalla-juego").style.display = "block";
    cargarBandera();

}

//funcion que carga la siguiente bandera y sus opciones
function cargarBandera(){
    //controlo sis se acabaron las banderas
    if(banderas.length <= posActual){
        terminarJuego();
    }
    else{//cargo las opciones
        //limpiamos las clases que se asignaron
        limpiarOpciones();

        document.getElementById("imgBandera").src = "img/" + banderas[posActual];
        document.getElementById("n0").innerHTML = opciones[posActual][0];
        document.getElementById("n1").innerHTML = opciones[posActual][1];
        document.getElementById("n2").innerHTML = opciones[posActual][2];
        document.getElementById("n3").innerHTML = opciones[posActual][3];
    }
}

function limpiarOpciones(){
    document.getElementById("n0").className = "nombre";
    document.getElementById("n1").className = "nombre";
    document.getElementById("n2").className = "nombre";
    document.getElementById("n3").className = "nombre";

    document.getElementById("l0").className = "letra";
    document.getElementById("l1").className = "letra";
    document.getElementById("l2").className = "letra";
    document.getElementById("l3").className = "letra";
}

function comprobarRespuesta(opElegida){
    if(opElegida==correcta[posActual]){//acertó
        //agregamos las clases para colocar el color verde a la opcion elegida
        document.getElementById("n" + opElegida).className = "nombre nombreAcertada";
        document.getElementById("l" + opElegida).className = "letra letraAcertada";
        cantidadAcertadas++;
    }else{//no acerto
        //agramos las clases para colocar en rojo la opcion elegida
        document.getElementById("n" + opElegida).className = "nombre nombreNoAcertada";
        document.getElementById("l" + opElegida).className = "letra letraNoAcertada";

        //opcion que era correcta
        document.getElementById("n" + correcta[posActual]).className = "nombre nombreAcertada";
        document.getElementById("l" + correcta[posActual]).className = "letra letraAcertada";
    }
    posActual++;
    //Esperamos 1 segundo y pasamos mostrar la siguiente bandera y sus opciones
    setTimeout(cargarBandera,1000);
}
function terminarJuego(){
    //ocultamos las pantallas y mostramos la pantalla final
    document.getElementById("pantalla-juego").style.display = "none";
    document.getElementById("pantalla-final").style.display = "block";
    //agreamos los resultados
    document.getElementById("numCorrectas").innerHTML = cantidadAcertadas;
    document.getElementById("numIncorrectas").innerHTML = banderas.length - cantidadAcertadas;
}

function volverAlInicio(){
    //ocultamos las pantallas y activamos la inicial
    document.getElementById("pantalla-final").style.display = "none";
    document.getElementById("pantalla-inicial").style.display = "block";
    document.getElementById("pantalla-juego").style.display = "none";
}
