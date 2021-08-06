<template>
  <div id="app">
    <b-navbar toggleable="lg" type="dark" variant="info">
      <img src="https://i.pinimg.com/originals/9a/36/b2/9a36b29d0adca32942408b411976ba0b.jpg" class="d-inline-block align-top" alt="Kitten" width="100" height="50">
<b-navbar-brand href="/about">Centro Médico Quito</b-navbar-brand> 
      <b-container>
    

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="/ingresarEspecialidad">Ingresar Especialidad</b-nav-item>
        <b-nav-item href="/ingresarEmpleado">Ingresar Empleado</b-nav-item>
        <b-nav-item href="/ingresarDoctor" >Ingresar Doctor</b-nav-item>
        <b-nav-item href="/ReubicarDoctor" >Reubicar Doctor</b-nav-item>
        <b-nav-item href="/NominaPago" >Nomina de pagos</b-nav-item>

      </b-navbar-nav>

      <!-- Right aligned nav items -->
      
    </b-collapse>
    </b-container>
  </b-navbar>
  <b-container>
    <router-view/>
    </b-container>
  </div>
</template>

