# PracticaPC3-CSS
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ejercicios de Transiciones y Animaciones</title>
    <link rel="stylesheet" href="estilo .css">
</head>
<body>

    <!-- Ejercicio 1: Botón CTA -->
    <section>
        <h2>Botón CTA</h2>
        <button class="btn-cta">
            Comprar Ahora
        </button>
    </section>

    <hr>

    <!-- Ejercicio 2: Enlace dinámico -->
    <section>
        <h2>Enlace de artículo</h2>
        <a href="#" class="article-link">
            Leer artículo completo
        </a>
    </section>

    <hr>

    <!-- Ejercicio 3: Input expandible -->
    <section>
        <h2>Búsqueda</h2>
        <input
            type="text"
            class="search-input"
            placeholder="Buscar..."
        >
    </section>

    <hr>

    <!-- Ejercicio 4: User Card -->
    <section>
        <h2>Usuario</h2>

        <div class="user-card">
            <h3>María López</h3>

            <div class="card-details">
                <p>Email: maria@email.com</p>
                <p>Rol: Administradora</p>
            </div>
        </div>
    </section>

    <hr>

    <!-- Ejercicio 5: Banner promocional -->
    <section>
        <div class="promo-banner">
            🎉 ¡Oferta especial del 30% de descuento!
        </div>
    </section>

    <hr>

    <!-- Ejercicio 6: Toast Notification -->
    <div class="toast-notification">
        ✅ Cambios guardados correctamente
    </div>

    <hr>

    <!-- Ejercicio 7: Cards con animación escalonada -->
    <section>
        <h2>Publicaciones</h2>

        <div class="post-item">
            <h3>Post 1</h3>
            <p>Contenido de la publicación.</p>
        </div>

        <div class="post-item">
            <h3>Post 2</h3>
            <p>Contenido de la publicación.</p>
        </div>

        <div class="post-item">
            <h3>Post 3</h3>
            <p>Contenido de la publicación.</p>
        </div>
    </section>

    <hr>

    <!-- Ejercicio 8: Botón icono -->
    <section>
        <h2>Acción</h2>

        <span class=    "btn-icon">
            ⚙️
        </span>
    </section>

    <hr>

    <!-- Ejercicio 9: Loader -->
    <section>
        <h2>Cargando datos</h2>

        <div class="spinner-loader"></div>
    </section>

    <hr>

    <!-- Ejercicio 10: Toolbar sticky -->
    <nav class="subnav-toolbar">
        <a href="#">Inicio</a>
        <a href="#">Productos</a>
        <a href="#">Servicios</a>
        <a href="#">Contacto</a>
    </nav>

</body>
</html>

// =========================================================================
// Solución Ejercicio 1: Botón CTA reactivo con delay explícito de 0.1s
// =========================================================================
.btn-cta {
  background-color: #2563eb;
  color: #ffffff;
  padding: 10px 22px;
  border: none;
  border-radius: 6px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
  cursor: pointer;
  // transition explícito: propiedad | duración | timing-function | delay
  transition: all 0.3s ease-out 0.1s;

  &:hover {
    background-color: #1d4ed8;
    transform: translateY(-3px);
    box-shadow: 0 6px 14px rgba(37, 99, 235, 0.25);
  }

  &:active {
    transform: translateY(-1px);
    box-shadow: 0 3px 6px rgba(37, 99, 235, 0.2);
  }
}

// =========================================================================
// Solución Ejercicio 2: Enlace de contenido con subrayado dinámico
// =========================================================================
.article-link {
  position: relative;
  display: inline-block;
  color: #0f172a;
  text-decoration: none;

  &::after {
    content: "";
    position: absolute;
    bottom: -2px;
    left: 0;
    width: 0%;
    height: 2px;
    background-color: #059669;
    transition: width 0.25s cubic-bezier(0.4, 0, 0.2, 1) 0.1s;
  }

  &:hover::after {
    width: 100%;
  }
}

// =========================================================================
// Solución Ejercicio 3: Input de búsqueda expandible con delay
// =========================================================================
.search-input {
  width: 160px;
  padding: 8px 12px;
  border: 1px solid #cbd5e1;
  border-radius: 4px;
  outline: none;
  transition: width 0.3s ease-in-out 0.1s, border-color 0.3s ease-in-out 0.1s;

  &:focus {
    width: 260px;
    border-color: #2563eb;
  }
}

// =========================================================================
// Solución Ejercicio 4: Revelado Suave de Metadatos en Ficha
// =========================================================================
.user-card {
  .card-details {
    opacity: 0;

    transition-property: opacity;
    transition-duration: 0.3s;
    transition-timing-function: ease;
    transition-delay: 0.1s;
  }

  &:hover .card-details {
    opacity: 1;
  }
}

// =========================================================================
// Solución Ejercicio 5: Banner con zoom y fade de entrada al cargar
// =========================================================================
@keyframes zoomFadeIn {
  0% {
    opacity: 0;
    transform: scale(0.9);
  }

  100% {
    opacity: 1;
    transform: scale(1);
  }
}

.promo-banner {
  background-color: #fef3c7;
  border: 1px solid #f59e0b;
  padding: 14px 18px;
  border-radius: 6px;
  // Invocación con duración, timing y fill-mode forwards para retención
  animation: zoomFadeIn 0.7s ease-out forwards;
}

// =========================================================================
// Solución Ejercicio 6: Alerta toast con desplazamiento horizontal
// =========================================================================
@keyframes slideInRight {
  0% {
    opacity: 0;
    transform: translateX(120%);
  }

  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

.toast-notification {
  position: fixed;
  bottom: 20px;
  right: 20px;
  background-color: #0f172a;
  color: #ffffff;
  padding: 12px 20px;
  border-radius: 8px;
  // Retardo deliberado de 0.4s para mostrar tras el render estructural
  animation: slideInRight 0.5s ease-out 0.4s forwards;
}

// =========================================================================
// Solución Ejercicio 7: Entrada escalonada de tarjetas con bucle @for
// =========================================================================
@keyframes fadeUpEntrance {
  from {
    transform: translateY(25px);
    opacity: 0;
  }

  to {
    transform: translateY(0);
    opacity: 1;
  }
}

.post-item {
  animation: fadeUpEntrance 0.6s ease-out both;
}

@for $i from 1 through 3 {
  .post-item:nth-child(#{$i}) {
    animation-delay: $i * 0.2s;
  }
}

// =========================================================================
// Solución Ejercicio 8: Mixin de transformación con prefijos cruzados
// =========================================================================
@mixin vendor-transform($val) {
  -webkit-transform: $val;
  -moz-transform: $val;
  transform: $val; // La propiedad estándar siempre al final
}

.btn-icon {
  display: inline-block;
  @include vendor-transform(rotate(0deg));
  transition: transform 0.25s ease-out 0.1s;

  &:hover {
    @include vendor-transform(rotate(45deg));
  }
}

// =========================================================================
// Solución Ejercicio 9: Mixin integral para animación con prefijos
// =========================================================================
@mixin vendor-animation($params) {
  -webkit-animation: $params;
  -moz-animation: $params;
  animation: $params;
}

@keyframes spinLoader {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

.spinner-loader {
  width: 30px;
  height: 30px;
  border: 3px solid #e2e8f0;
  border-top-color: #2563eb;
  border-radius: 50%;
  @include vendor-animation(spinLoader 1s linear infinite);
}

// =========================================================================
// Solución Ejercicio 10: Barra de herramientas fija con fallback
// ========================================================================
.subnav-toolbar {
  position: relative;

  @supports (position: sticky) or (position: -webkit-sticky) {
    position: sticky;
    top: 0;
  }
}