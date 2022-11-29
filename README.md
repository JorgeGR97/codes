<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        class Persona {
            constructor(nombre = "Pepe", apellidos = "unos", direccion = "su casa", fechaNac = "1/1/2000", genero = "binario", codigoPostal = "28800") {
                this._nombre = nombre;
                this._apellidos = apellidos;
                this._direccion = direccion;
                this._fechaNac = fechaNac;
                this._genero = genero;
                this._codigoPostal = codigoPostal;
            }
            get nombre() {
                return this._nombre;
            }
            get apellidos() {
                return this._apellidos;
            }
            get direccion() {
                return this._direccion;
            }
            get fechaNac() {
                return this._fechaNac;
            }
            get genero() {
                return this._genero;
            }
            get codigoPostal() {
                return this._codigoPostal;
            }
            set nombre(valor) {
                this._nombre = valor;
            }
            set apellidos(valor) {
                this._apellidos = valor;
            }
            set direccion(valor) {
                this._direccion = valor;
            }
            set fechaNac(valor) {
                this._fechaNac = valor;
            }
            set genero(valor) {
                this._genero = valor;
            }
            set codigoPostal(valor) {
                this._codigoPostal = valor;
            }

            edad() {
                var fecha = this.fechaNac.split("/");
                var fechaNacimiento = new Date(parseInt(fecha[2]), parseInt(fecha[1]), parseInt(fecha[0]));
                var fechaActual = new Date();
                var edad = fechaActual.getFullYear() - fechaNacimiento.getFullYear();
                var mes = fechaActual.getMonth() - fechaNacimiento.getMonth();
                if (mes < 0 || (mes === 0 && fechaActual.getDate() < fechaNacimiento.getDate())) {
                    //Sacar una alerta
                    alert("La fecha de nacimiento no puede ser posterior a la fecha actual");
                }
                return edad;
            }

            senorSenora() {
                if (this._genero == "Masculino") {
                    return "Sr. ";
                }
                else if (this._genero == "Femenino") {
                    return "Sra. ";
                }
            }

            listarPersona() {
                var salida = "";
                salida = "<table border = 2> <tr> <th> NOMBRE Y APELLIDOS </th> <th> DIRECCION </th> <th> FECHA NACIMIENTO </th> <th> EDAD </th> <th> CODIGO POSTAL </th> </tr>";
                salida += "<tr> <td>" + this.senorSenora() + " " + this.nombre + " " + this.apellidos + "</td> <td>" + this.direccion + "</td> <td>" + this.fechaNac + "</td> <td>" + this.edad() + "</td> <td>" + this.codigoPostal + "</td> </tr>";
                salida += "</table>";
                var miVentana = window.open("", "ventana", "width = 600, height = 400, top = 200, left = 200");
                miVentana.document.open();
                miVentana.document.write("<html>");
                miVentana.document.write("<head>");
                miVentana.document.write("<title> Listado en ventana </title>");
                miVentana.document.write("</head>");
                miVentana.document.write("<body>");
                miVentana.document.write("<center>");
                miVentana.document.write("Listado de una persona");
                miVentana.document.write("<br> <br>");
                miVentana.document.write(salida);
                miVentana.document.write("<br> <input type = 'button' value = 'Cerrar ventana' onclick = 'window.close();'");
                miVentana.document.write("</center>");
                miVentana.document.write("</body>");
                miVentana.document.write("</html>");
                miVentana.document.close();
            }

            static listarPersonas(tabla) {
                var salida = "";
                salida = "<table border = 2> <tr> <th> NOMBRE Y APELLIDOS </th> <th> DIRECCION </th> <th> FECHA NACIMIENTO </th> <th> EDAD </th> <th> CODIGO POSTAL </th> </tr>";
                for (var elem of tabla) {
                    salida += "<tr> <td>" + elem.senorSenora() + " " + elem.nombre + " " + elem.apellidos + "</td> <td>" + elem.direccion + "</td> <td>" + elem.fechaNac + "</td> <td>" + elem.edad() + "</td> <td>" + elem.codigoPostal + "</td> </tr> </br>";
                }
                salida += "</table>";
                var miVentana = window.open("", "ventana", "width = 600, height = 400, top = 200, left = 200");
                miVentana.document.open();
                miVentana.document.write("<html>");
                miVentana.document.write("<head>");
                miVentana.document.write("<title> Listado en ventana </title>");
                miVentana.document.write("</head>");
                miVentana.document.write("<body>");
                miVentana.document.write("<center>");
                miVentana.document.write("Listado Array de personas");
                miVentana.document.write("<br> <br>");
                miVentana.document.write(salida);
                miVentana.document.write("<br> <input type = 'button' value = 'Cerrar ventana' onclick = 'window.close();'");
                miVentana.document.write("</center>");
                miVentana.document.write("</body>");
                miVentana.document.write("</html>");
                miVentana.document.close();
            }
        }
    </script>
</head>

<body>
    <p> Nombre: <input type="text" id="nombre" />
    <div id="errNombre"></div>
    </p>
    <p> Apellidos: <input type="text" id="apellidos" />
    <div id="errApellidos"></div>
    </p>
    <p> Direccion: <input type="text" id="direccion" />
    <div id="errDireccion"></div>
    </p>
    <p> Fecha de nacimiento: <input type="text" id="fecha" />
    <div id="errFecha"></div>
    </p>
    <p> Genero: <input type="text" id="genero" />
    <div id="errGenero"></div>
    </p>
    <p> Codigo postal: <input type="text" id="codigoPostal" />
    <div id="errCodigo"></div>
    </p>
    <p>
    <div id="divBtn">
        <input type="button" onclick="primera()" value="Primera" id="uno" />
        <input type="button" onclick="anterior()" value="&lt;&lt; Anterior" id="dos" />
        <input type="button" onclick="siguiente()" value="Siguiente &gt;&gt;" id="tres" />
        <input type="button" onclick="ultima()" value="Última" id="cuatro" />
        <div>
            <p>
                <input type="button" onclick="alta()" value="Alta" id="btnAlta" />
                <input type="button" onclick="baja()" value="Baja" id="btnBaja" />
                <input type="button" onclick="modificacion()" value="Modificacion" id="btnModificacion" />
                <input type="button" onclick="listarUnaPersona()" value="Listado una persona" id="btnPersona">
                <input type="button" onclick="listarTodasLasPersonas()" value="Listado todos los Humanos" />
                <input type="button" onclick="aceptar()" value="Aceptar" id="btnAcep" />
                <input type="button" onclick="cancelar()" value="Cancelar" id="btnCancel" />

</body>
<script>
    var posicion = 0;
    var misHumanos = [];
    let persona1 = new Persona("Andres", "Perez", "C/ Calle mayor", "04/08/1994", "Masculino", "42145");
    let persona2 = new Persona("Juan", "Fernandez", "C/ Calle menor", "21/01/1983", "Masculino", "31451");
    let persona3 = new Persona("Marta", "Garcia", "Avenida constitucion", "17/05/1997", "Femenino", "45151");
    let persona4 = new Persona("Jorge", "Gomez", "C/ Fernando VI", "17/04/2004", "Masculino", "51512");
    misHumanos.push(persona1);
    misHumanos.push(persona2);
    misHumanos.push(persona3);
    misHumanos.push(persona4);
    primera();

    function listarUnaPersona() {
        misHumanos[posicion].listarPersona();
    }
    function listarTodasLasPersonas() {
        Persona.listarPersonas(misHumanos);
    }
    function limpiar() {
        document.getElementById("nombre").value = "";
        document.getElementById("apellidos").value = "";
        document.getElementById("direccion").value = "";
        document.getElementById("fecha").value = "";
        document.getElementById("genero").value = "";
        document.getElementById("codigoPostal").value = "";
    }
    function limpiarDivs() {
        document.getElementById('errNombre').innerHTML = '';
        document.getElementById('errApellidos').innerHTML = '';
        document.getElementById('errDireccion').innerHTML = '';
        document.getElementById('errFecha').innerHTML = '';
        document.getElementById('errGenero').innerHTML = '';
        document.getElementById('errCodigo').innerHTML = '';
    }
    var accionAceptar = 0;
    function alta() {
        navegador(true);
        botones(true, 'visible');
        limpiar();
        accionAceptar = 1;
    }
    function baja() {
        navegador(true);
        botones(true, 'visible');
        accionAceptar = 2;
    }
    function modificacion() {
        navegador(true);
        botones(true, 'visible');
        accionAceptar = 3;
    }
    function aceptar(value) {
        limpiarDivs();
        if (accionAceptar == 1) {
            crearPersona();
        }
        else if (accionAceptar == 2) {
            eliminarPersona();
        }
        else if (accionAceptar == 3) {
            modificarPersona();
        }
    }
    function cancelar() {
        mostrarBotones();
        mostrarArray();
        limpiar();
    }
    function crearPersona() {
        if (validarNombre() && validarApellidos() && validarDireccion() && validarGenero() && validarCodigopostal() && validarFecha()) {
            var respuestaUsuario = confirm('Estas Seguro ?');
            if (respuestaUsuario) {
                let nombre = document.getElementById("nombre").value.trim();
                let apellidos = document.getElementById("apellidos").value.trim();
                let direccion = document.getElementById("direccion").value.trim();
                let fechaNacimiento = document.getElementById("fecha").value.trim();
                //Comprueba si el genero es masculino o femenino
                let genero;
                let generoInt = document.getElementById("genero").value.trim();
                if (generoInt == "masculino") {
                    genero = "Masculino";
                } else {
                    genero = "Femenino";
                }
                let codigoPostal = document.getElementById("codigoPostal").value.trim();
                let persona = new Persona(nombre, apellidos, direccion, fechaNacimiento, genero, codigoPostal);
                //Añadimos la persona al array
                misHumanos.push(persona);

                //Limpiar los campos
                limpiar();
                primera();
                mostrarBotones();
            } else {
                alert('No he añadido nada al array');
            }
        }
    }
    function eliminarPersona() {
        var confirma = confirm("Realmente quiere eliminar a la persona?")
        if (confirma) {
            misHumanos.splice(posicion, 1);
            primera();
        } else {
            alert('No se ha realizado la baja en el array');

        }
        mostrarBotones();
    }

    function modificarPersona() {
        if (validarNombre() && validarApellidos() && validarDireccion() && validarGenero() && validarCodigopostal() && validarFecha()) {
            var respuestaUsuario = confirm('Quiere realizar la modificacion?');
            if (respuestaUsuario) {
                let nombre = document.getElementById("nombre").value.trim();
                let apellidos = document.getElementById("apellidos").value.trim();
                let direccion = document.getElementById("direccion").value.trim();
                let fechaNacimiento = document.getElementById("fecha").value.trim();
                //Comprueba si el genero es masculino o femenino
                let genero;
                let generoInt = document.getElementById("genero").value.trim();
                if (generoInt == "masculino") {
                    genero = "Masculino";
                } else {
                    genero = "Femenino";
                }
                let codigoPostal = document.getElementById("codigoPostal").value.trim();
                misHumanos[posicion].nombre = nombre;
                misHumanos[posicion].apellidos = apellidos;
                misHumanos[posicion].direccion = direccion;
                misHumanos[posicion].fechaNac = fechaNacimiento;
                misHumanos[posicion].genero = genero;
                misHumanos[posicion].codigoPostal = codigoPostal;
                mostrarBotones();
                primera();
            } else {
                alert('No se ha modificado la persona del array');

            }
        }

    }
    function navegador(valor) {
        document.getElementById("uno").disabled = valor;
        document.getElementById("dos").disabled = valor;
        document.getElementById("tres").disabled = valor;
        document.getElementById("cuatro").disabled = valor;
    }
    function botones(valor1, valor2) {
        document.getElementById("btnAlta").disabled = valor1;
        document.getElementById("btnBaja").disabled = valor1;
        document.getElementById("btnModificacion").disabled = valor1;
        document.getElementById("btnAcep").style.visibility = valor2;
        document.getElementById("btnCancel").style.visibility = valor2;
    }
    function mostrarBotones() {
        navegador(false);
        botones(false, 'hidden');
    }

    function mostrarArray(posicion) {
        document.getElementById("nombre").value = misHumanos[posicion]._nombre;
        document.getElementById("apellidos").value = misHumanos[posicion]._apellidos;
        document.getElementById("direccion").value = misHumanos[posicion]._direccion;
        document.getElementById("fecha").value = misHumanos[posicion]._fechaNac;
        document.getElementById("genero").value = misHumanos[posicion]._genero;
        document.getElementById("codigoPostal").value = misHumanos[posicion]._codigoPostal;

        document.getElementById("btnAcep").style.visibility = 'hidden';
        document.getElementById("btnCancel").style.visibility = 'hidden';
        if (posicion == misHumanos.length - 1) {
            document.getElementById("tres").disabled = true;
            document.getElementById("cuatro").disabled = true;
        } else {
            document.getElementById("tres").disabled = false;
            document.getElementById("cuatro").disabled = false;
        }
        if (posicion == 0) {
            document.getElementById("uno").disabled = true;
            document.getElementById("dos").disabled = true;
        } else {
            document.getElementById("uno").disabled = false;
            document.getElementById("dos").disabled = false;
        }
    }
    function primera() {
        posicion = 0;
        mostrarArray(posicion);
    }

    function ultima() {
        posicion = misHumanos.length - 1;
        mostrarArray(posicion);
    }

    function anterior() {
        if (posicion > 0) {
            posicion--;
            mostrarArray(posicion);
        }
    }

    function siguiente() {
        if (posicion < misHumanos.length - 1) {
            posicion++;
            mostrarArray(posicion);
        }
    }


    function validarNombre() {
        let texto = document.getElementById('errNombre');
        var nombre = document.getElementById("nombre").value.trim().toLowerCase();
        var validos = "abcdefghijklmnopqrstuvwyz ";
        var cadenaOk = true;
        var ok = true;

        if (nombre.length >= 3 && nombre.length <= 20) {
            for (var i = 0; i < nombre.length; i++) {
                if (validos.indexOf(nombre.charAt(i)) == -1) {
                    cadenaOk = false;
                }
            }
            if (!cadenaOk) {
                texto.innerHTML = "El nombre es erróneo";
                texto.style.color = "red";
                ok = false;
            }

        }
        else {
            texto.innerHTML = "El nombre tiene menos de 3 o mas de 20 caracteres";
            texto.style.color = "red";
            ok = false;
        }

        return ok;
    }

    function validarApellidos() {
        let texto = document.getElementById("errApellidos");
        var apellidos = document.getElementById("apellidos").value.trim().toLowerCase();
        var validos = "abcdefghijklmnopqrstuvwyz ";
        var cadenaOk = true;
        var ok = true;

        for (var i = 0; i < apellidos.length; i++) {
            if (validos.indexOf(apellidos.charAt(i)) == -1) {
                cadenaOk = false;
            }
        }
        if (!cadenaOk) {
            texto.innerHTML = "Los apellidos son erróneo";
            texto.style.color = "red";
            ok = false;
        }
        if ((apellidos.length >= 30) || (apellidos.length < 3)) {
            texto.innerHTML = "Los apellidos tiene menos de 3 o más de 30 caracteres";
            texto.style.color = "red";
            ok = false;
        }
        return ok;
    }

    function validarFecha() {
        var texto = document.getElementById("errFecha");
        var fechaCompleta;
        var fecha = document.getElementById("fecha").value;
        var barra = document.getElementById("fecha").value.indexOf("/");
        var arrayFecha = fecha.split("/");
        var fechaDia = parseInt(arrayFecha[0]);
        var fechaMes = parseInt(arrayFecha[1]);
        var fechaAno = parseInt(arrayFecha[2]);
        var ok = true;
        if (barra >= 0) {
            if (fechaDia <= 0 || fechaDia > 31 || fechaMes <= 0 || fechaMes > 12 || fechaAno <= 1900 || fechaAno > 2022) {
                texto.innerHTML = "Fecha Incorrecta";
                texto.style.color = "red";
                ok = false;
            }
        }
        else {
            texto.innerHTML = "Formato de fecha incorrecto";
            texto.style.color = "red";
            ok = false;
        }
        return ok;
    }

    function validarDireccion() {
        let texto = document.getElementById("errFecha");
        var direccion = document.getElementById("direccion").value.trim().toLowerCase();
        var validos = "abcdefghijklmnopqrstuvwyz0123456789 ";
        var cadenaOk = true;
        var ok = true;

        for (var i = 0; i < direccion.length; i++) {
            if (validos.indexOf(direccion.charAt(i)) == -1) {
                cadenaOk = false;
            }
        }
        if (!cadenaOk) {
            texto.innerHTML = "La direccion es erronea";
            texto.style.color = "red";
            ok = false;
        }
        if ((direccion.length >= 30) || (direccion.length < 3)) {
            texto.innerHTML = "La direccion tiene menos de 3 o más de 35 caracteres";
            texto.style.color = "red";
            ok = false;
        }
        return ok;
    }


    function validarGenero() {
        let texto = document.getElementById("errGenero");
        var genero = document.getElementById("genero").value.trim().toLowerCase();
        var ok;
        if (genero === "masculino" || genero === "femenino") {
            ok = true;
        }
        else {
            ok = false;
            texto.innerHTML = "Valores introducidos no validos";
            texto.style.color = "red";
        }
        return ok;
    }

    function validarCodigopostal() {
        let texto = document.getElementById("errCodigo");
        var codigoPostal = document.getElementById("codigoPostal").value.trim().toLowerCase();
        var validos = "0123456789";
        var cadenaOk = true;
        var ok = true;

        for (var i = 0; i < codigoPostal.length; i++) {
            if (validos.indexOf(codigoPostal.charAt(i)) == -1) {
                cadenaOk = false;
            }
        }
        if (!cadenaOk) {
            texto.innerHTML = "El codigo postal es erroneo";
            texto.style.color = "red";
            ok = false;
        }

        if (codigoPostal.length != 5) {
            texto.innerHTML = "La direccion no tiene 5 caracteres";
            texto.style.color = "red";
            ok = false;
        }

        return ok;
    }
</script>

</html>
