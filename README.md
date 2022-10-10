

datos = [

];

let id = null
let bd = false


function traerDatos() {
    datos.forEach(dato => {
        document.getElementById("datos").innerHTML += `
        <div class="card" style="width: 17rem;background-color:#f7f1e3; box-shadow: 5px 5px 10px ;  " >
        <div class="card-body" >
        <img style="border-radius:10px;" src="${dato.raza}.jpg" class="card-img-top" alt="..."> <br> <br>
          <p class="card-text" >
<b style="font-size:25px; font-family: Georgia, 'Times New Roman', Times, serif;" >${dato.nombre}</b> <br>
<b>Propietario:</b> ${dato.propietario}<br>
<b>Telefono:</b> ${dato.telefono}<br>
<b>Fecha:</b> ${dato.fecha}<br>
<b>Hora:</b> ${dato.hora}<br>
<b>Sintomas: </b>${dato.sintomas} <br><br>

<input id="edi" class="btn btn-dark"  onclick=editar(${JSON.stringify(dato).toString()}) type="button" value="Editar🔧" >

<input class="btn " style="background-color:#2bcbba; color:#fff;" onclick=eliminar(${dato.id}) type="button" value="Eliminar❌">

          </p>
     
        </div>
      </div>
      <br>
        `
    });
}



function editar(p) {
    bd = true
    id = p.id
    console.log(p);
    document.getElementById("nombre").value = p.nombre
    document.getElementById("propietario").value = p.propietario
    document.getElementById("telefono").value = p.telefono
    document.getElementById("fecha").value = p.fecha
    document.getElementById("hora").value = p.hora
    document.getElementById("sintomas").value = p.sintomas
    document.getElementById("raza").value = p.raza

}




function edicion() {

    if (bd === true && document.getElementById("nombre").value != "" && document.getElementById("propietario").value != ""
        && document.getElementById("telefono").value != "" && document.getElementById("fecha").value != ""
        && document.getElementById("hora").value != "" && document.getElementById("sintomas").value != "") {
        datos.forEach(dato => {
            if (dato.id == id) {
                dato.nombre = document.getElementById("nombre").value
                dato.propietario = document.getElementById("propietario").value
                dato.telefono = document.getElementById("telefono").value
                dato.fecha = document.getElementById("fecha").value
                dato.hora = document.getElementById("hora").value
                dato.sintomas = document.getElementById("sintomas").value
                dato.raza = document.getElementById("raza").value
            }
        })

        console.log(datos);
        document.getElementById("datos").innerHTML = ""
        traerDatos()
        vaciar()

        bd = false
        id = null



    } else {

        validacion()

    }

}

function agregar() {

    datos.push(
        {
            id: datos.length + 1,
            nombre: document.getElementById("nombre").value,
            propietario: document.getElementById("propietario").value,
            telefono: document.getElementById("telefono").value,
            fecha: document.getElementById("fecha").value,
            hora: document.getElementById("hora").value,
            sintomas: document.getElementById("sintomas").value,
            raza: document.getElementById("raza").value


        }
    )

    console.log(datos);
    document.getElementById("datos").innerHTML = ""
    traerDatos()
    vaciar()

}



function vaciar() {
    document.getElementById("nombre").value = ""
    document.getElementById("propietario").value = ""
    document.getElementById("telefono").value = ""
    document.getElementById("fecha").value = ""
    document.getElementById("hora").value = ""
    document.getElementById("sintomas").value = ""
    document.getElementById("raza").value = ""

}


function eliminar(i) {
    console.log(i);
    let pos = datos.findIndex(e =>
        e.id == i
    )
    console.log(pos);

    datos.splice(pos, 1)
    document.getElementById("datos").innerHTML = ""
    traerDatos()
    vaciar()


}


function validacion() {

    if (nombre.value === "" || nombre.value === null) {
        document.getElementById("alertError").innerHTML = `
        <div class="alert alert-danger" role="alert">
        👽 Llena la casilla de nombre, gracias.
      </div>
        `

        setTimeout(() => {
            document.getElementById("alertError").innerHTML = ""
        }, 2000);

        return dato.nombre = document.getElementById("nombre").value
    }



    if (propietario.value === "" || propietario.value === null) {

        document.getElementById("alertError").innerHTML = `
        <div class="alert alert-danger" role="alert">
        👽 Llena la casilla de propietario, gracias.
      </div>
        `

        setTimeout(() => {
            document.getElementById("alertError").innerHTML = ""
        }, 2000);

        return dato.propietario = document.getElementById("propietario").value
    }


    if (telefono.value === "" || telefono.value === null) {
        document.getElementById("alertError").innerHTML = `
        <div class="alert alert-danger" role="alert">
        👽 Llena la casilla de telefono, gracias.
      </div>
        `

        setTimeout(() => {
            document.getElementById("alertError").innerHTML = ""
        }, 2000);
        return dato.telefono = document.getElementById("telefono").value
    }


    if (fecha.value === "" || fecha.value === null) {
        document.getElementById("alertError").innerHTML = `
        <div class="alert alert-danger" role="alert">
        👽 Llena la casilla de fecha, gracias.
      </div>
        `

        setTimeout(() => {
            document.getElementById("alertError").innerHTML = ""
        }, 2000);
        return dato.fecha = document.getElementById("fecha").value
    }


    if (hora.value === "" || hora.value === null) {
        document.getElementById("alertError").innerHTML = `
        <div class="alert alert-danger" role="alert">
        👽 Llena la casilla de hora, gracias.
      </div>
        `

        setTimeout(() => {
            document.getElementById("alertError").innerHTML = ""
        }, 2000);
        return dato.hora = document.getElementById("hora").value
    }



    if (raza.value === "" || raza.value === null) {
        document.getElementById("alertError").innerHTML = `
        <div class="alert alert-danger" role="alert">
        👽 Elije la raza, gracias.
      </div>
        `

        setTimeout(() => {
            document.getElementById("alertError").innerHTML = ""
        }, 2000);
        return dato.sintomas = document.getElementById("sintomas").value
    }




    if (sintomas.value === "" || sintomas.value === null) {
        document.getElementById("alertError").innerHTML = `
        <div class="alert alert-danger" role="alert">
        👽 Llena la casilla de sintomas, gracias.
      </div>
        `

        setTimeout(() => {
            document.getElementById("alertError").innerHTML = ""
        }, 2000);
        return dato.sintomas = document.getElementById("sintomas").value
    }


    if (nombre.value != "" && propietario.value != "" && telefono.value != "" && fecha.value != "" && hora.value != "" && sintomas.value != "") {
        agregar()

        document.getElementById("alertOk").innerHTML = `
        <div class="alert alert-success" role="alert">
        👽 Guardado exitoso.
        </div>
        `

        setTimeout(() => {
            document.getElementById("alertOk").innerHTML = ""
        }, 2000);

    }

}




