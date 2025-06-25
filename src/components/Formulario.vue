<template>
    <div class="container">
    <h1>Crear Nuevo Usuario</h1>
      <form class="=form">
        <div class="form-group">
          <label for="username">Nombre de Usuario </label>
          <input type="text" id="username">
        </div>

        <div class="form-group">
          <label for="email">Correo Electronico </label>
          <input type="email" id="email">
        </div>

        <div class="form-group">
          <label for="birthdate">Fecha de Nacimiento </label>
          <input type="date" id="birthdate">
        </div>

        <button type="submit">Crear Usuario</button>
      </form>

      <div class="user-data-box">
        <h2>Datos del Usuario</h2>
        <p>Nombre: </p>
        <p>Email: </p>
        <p>Edad: </p>
      </div>


    </div>

  </template>
  
  <script>
  export default {
    data() {
      return {
        usuario: {
          nombre: '',
          email: '',
          contrasena: '',
          fechaNacimiento: '',
        },
        mostrarDatos: false,
      };
    },
    methods: {
      calcularEdad() {
        if (!this.usuario.fechaNacimiento) return '';
        const nacimiento = new Date(this.usuario.fechaNacimiento);
        const hoy = new Date();
        let edad = hoy.getFullYear() - nacimiento.getFullYear();
        const mes = hoy.getMonth() - nacimiento.getMonth();
        if (mes < 0 || (mes === 0 && hoy.getDate() < nacimiento.getDate())) {
          edad--;
        }
        return edad;
      },
      crearUsuario() {
        alert(`Usuario creado con éxito:
        Nombre: ${this.usuario.nombre}
        Email: ${this.usuario.email}
        Edad: ${this.calcularEdad()} años`);
        this.mostrarDatos = true;
        this.limpiarFormulario();
      },
      limpiarFormulario() {
        this.usuario = {
          nombre: '',
          email: '',
          contrasena: '',
          fechaNacimiento: '',
        };
      },
    },
  };
  </script>
  
  <style>
  body {
    font-family: Arial, sans-serif;
  }
  
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    background-color: #1e1e1e;
    color: white;
  }

  h1, h2 {
    text-align: center;
  }

  .form {
    background-color: #2b2b2b;
    padding: 20px;
    border-radius: 8px;
    width: 100%;
    max-width: 400px;
  }

  .form-group{
    display: flex;
    flex-direction: column;
    margin-bottom: 15px;
  }

  .form-group label {
    margin-bottom: 5px;
  }

  input {
    padding: 8px;
    border-radius: 4px;
    border: none;
  }

  button{
    background-color: #007bff;
    color: #fff;
    padding: 10px;
    border: none;
    width: 100%;
    border-radius: 5px;
    cursor: pointer;
  }

  .user-data-box {
    background-color: #2b2b2b;
    padding: 20px;
    border: 1px solid #888;
    border-radius: 8px;
    max-width: 400px;
    width: 100%;
    margin-top: 20px;
  }



  </style>