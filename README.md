<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="E-commerce dinámico con JS. Explora y compra productos increíbles con nuestro carrito interactivo.">
    <meta name="keywords" content="e-commerce, tienda online, javascript, html, css, bootstrap">
    <title>E-Commerce Dinámico - Tu Tienda Online</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;700&display=swap" rel="stylesheet">
    
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header class="sticky-top">
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
            <div class="container">
                <a class="navbar-brand" href="#">🛒 **Mi Tienda**</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarNav">
                    <ul class="navbar-nav ms-auto">
                        <li class="nav-item"><a class="nav-link" href="#inicio">Inicio</a></li>
                        <li class="nav-item"><a class="nav-link" href="#productos">Productos</a></li>
                        <li class="nav-item"><a class="nav-link" href="#reseñas">Reseñas</a></li>
                        <li class="nav-item"><a class="nav-link" href="#contacto">Contacto</a></li>
                        <li class="nav-item">
                            <button class="btn btn-warning ms-lg-3" data-bs-toggle="modal" data-bs-target="#cartModal">
                                <i class="fas fa-shopping-cart"></i> Carrito (<span id="cart-counter">0</span>)
                            </button>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    </header>

    <main>
        <section id="inicio" class="py-5 text-center bg-light">
            <div class="container">
                <h1 class="display-4 mb-4">¡Bienvenidos a Mi Tienda!</h1>
                <p class="lead">Lo mejor en tecnología y accesorios, directamente a tu casa.</p>
                
                <div class="ratio ratio-16x9 mx-auto" style="max-width: 800px;">
                    <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ?controls=0" title="Video de Promoción" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>
            </div>
        </section>

        <section id="productos" class="py-5">
            <div class="container">
                <h2 class="text-center mb-5">Productos Destacados</h2>
                <div id="products-container" class="row g-4">
                    </div>
            </div>
        </section>

        <section id="reseñas" class="py-5 bg-light">
            <div class="container">
                <h2 class="text-center mb-5">Opiniones de Nuestros Clientes</h2>
                <div class="reviews-grid">
                    <div class="card p-3 shadow-sm">
                        <p class="fst-italic">"¡Excelente calidad y envío rápido! El mejor sitio web de e-commerce que he usado."</p>
                        <footer class="blockquote-footer">Ana M.</footer>
                    </div>
                    <div class="card p-3 shadow-sm">
                        <p class="fst-italic">"La interfaz es muy fácil de usar. La función del carrito es super intuitiva."</p>
                        <footer class="blockquote-footer">Carlos G.</footer>
                    </div>
                    <div class="card p-3 shadow-sm">
                        <p class="fst-italic">"Me encantaron los productos. Definitivamente volveré a comprar aquí."</p>
                        <footer class="blockquote-footer">Sofía L.</footer>
                    </div>
                </div>
            </div>
        </section>

        <section id="contacto" class="py-5">
            <div class="container">
                <h2 class="text-center mb-4">Contáctanos</h2>
                <div class="row justify-content-center">
                    <div class="col-lg-8">
                        <form id="contact-form" action="https://formspree.io/f/tu-id-de-formspree" method="POST" class="p-4 border rounded shadow-lg">
                            <div class="mb-3">
                                <label for="nombre" class="form-label">Nombre</label>
                                <input type="text" class="form-control" id="nombre" name="nombre" required>
                                <div class="invalid-feedback">Por favor, ingresa tu nombre.</div>
                            </div>
                            <div class="mb-3">
                                <label for="email" class="form-label">Correo Electrónico</label>
                                <input type="email" class="form-control" id="email" name="email" required>
                                <div class="invalid-feedback" id="email-feedback">Por favor, ingresa un correo electrónico válido.</div>
                            </div>
                            <div class="mb-3">
                                <label for="mensaje" class="form-label">Mensaje</label>
                                <textarea class="form-control" id="mensaje" name="mensaje" rows="4" required></textarea>
                                <div class="invalid-feedback">El mensaje no puede estar vacío.</div>
                            </div>
                            <button type="submit" class="btn btn-primary w-100">Enviar Mensaje</button>
                            <div id="form-status" class="mt-3 text-center d-none"></div>
                        </form>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <div class="modal fade" id="cartModal" tabindex="-1" aria-labelledby="cartModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-lg">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="cartModalLabel">🛍️ Tu Carrito de Compras</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Cerrar"></button>
          </div>
          <div class="modal-body">
            <div id="cart-items-list" class="list-group">
                <p id="empty-cart-message" class="text-center text-muted">El carrito está vacío.</p>
            </div>
            <h4 class="mt-4 text-end">Total: $<span id="cart-total">0.00</span></h4>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Seguir Comprando</button>
            <button type="button" class="btn btn-success" id="checkout-button">Pagar</button>
          </div>
        </div>
      </div>
    </div>

    <footer class="bg-dark text-white py-4">
        <div class="container text-center">
            <p>&copy; 2025 Mi Tienda E-Commerce. Todos los derechos reservados.</p>
            <p>
                <a href="#" class="text-white mx-2"><i class="fab fa-facebook"></i></a>
                <a href="#" class="text-white mx-2"><i class="fab fa-instagram"></i></a>
            </p>
        </div>
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
    
    <script src="script.js"></script>
</body>
</html>

# 🛒 E-Commerce Dinámico - Mi Tienda

Este es un proyecto de sitio web de e-commerce interactivo desarrollado con HTML, CSS, y JavaScript.

## Propósito

El objetivo principal de este proyecto es demostrar la capacidad de crear una aplicación web **dinámica** que:

1.  **Consume una API REST** para obtener y mostrar una lista de productos.
2.  Implementa la funcionalidad completa de un **Carrito de Compras** que persiste los datos usando `localStorage`.
3.  Utiliza **Bootstrap, Flexbox y CSS Grid** para un diseño atractivo y **responsivo**.
4.  Incluye un **Formulario de Contacto** funcional (usando Formspree).

## Tecnologías Utilizadas

* **HTML5** (Semántico)
* **CSS3** (Flexbox, Grid, Media Queries)
* **Bootstrap 5** (Framework de Diseño)
* **JavaScript (ES6+)**
* **Fetch API** (Para la conexión REST)
* **localStorage** (Para el carrito)

## Características

* Visualización de productos desde una API.
* Funcionalidad de "Añadir al Carrito" con contador dinámico.
* Edición de cantidades y eliminación de ítems en el carrito.
* Diseño adaptable a móviles y escritorio.
* Validación de formularios en el cliente.

/* 3. Estilos Básicos (Fuentes, Header, Footer, Background) */

body {
    font-family: 'Poppins', sans-serif; /* Google Fonts */
    background-color: #f8f9fa;
}

/* Header */
header {
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Footer */
footer {
    background-color: #343a40 !important; /* Estilo de Bootstrap Dark */
}

/* Background aplicado a una sección */
#inicio {
    background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%); /* Degradado */
}


/* 4. Diseño Responsivo con Flexbox y Grid */

/* --- Sección Productos (Uso de Flexbox para Cards - Ya implementado por Bootstrap .row y .col) --- */
/* Las clases 'row' y 'col' de Bootstrap usan Flexbox para organizar las tarjetas. */

/* Ajuste del tamaño de las imágenes de producto */
.product-card-img {
    height: 200px; /* Altura fija para uniformidad */
    object-fit: cover; /* Asegura que la imagen cubra el área sin distorsionarse */
}

/* --- Sección Reseñas (Uso de CSS Grid) --- */
.reviews-grid {
    display: grid;
    /* Por defecto: una columna para móviles */
    grid-template-columns: 1fr; 
    gap: 20px;
    padding: 0 15px;
}

/* Media Query para escritorio/tableta (Grid con 3 columnas) */
@media (min-width: 768px) {
    .reviews-grid {
        /* Tres columnas de igual tamaño */
        grid-template-columns: repeat(3, 1fr); 
    }
}

/* --- Sección Contacto (Uso de Media Queries para adaptabilidad) --- */
#contacto .p-4 {
    transition: all 0.3s ease;
}

/* Media Query para pantallas pequeñas (ajuste de padding) */
@media (max-width: 576px) {
    #contacto .p-4 {
        padding: 1.5rem !important; /* Más pequeño en móvil */
        margin: 0 10px;
    }
}

// Constante para la API de prueba de productos (JSONPlaceholder ofrece una estructura similar)
const API_URL = 'https://jsonplaceholder.typicode.com/posts'; // Usaremos esto como base, luego simularemos datos de productos

// Selectores del DOM
const productsContainer = document.getElementById('products-container');
const cartCounter = document.getElementById('cart-counter');
const cartItemsList = document.getElementById('cart-items-list');
const cartTotalElement = document.getElementById('cart-total');
const emptyCartMessage = document.getElementById('empty-cart-message');
const contactForm = document.getElementById('contact-form');
const emailInput = document.getElementById('email');

// Inicializar el carrito desde localStorage
let cart = JSON.parse(localStorage.getItem('ecommerceCart')) || [];

// --- Función de Productos de Mock (Simulación de Datos de Producto) ---
const mockProducts = [
    { id: 1, title: 'Auriculares Bluetooth Pro', price: 89.99, image: 'https://via.placeholder.com/400x200?text=Auriculares+Pro', description: 'Sonido de alta fidelidad con cancelación de ruido.' },
    { id: 2, title: 'Mouse Gamer RGB', price: 45.50, image: 'https://via.placeholder.com/400x200?text=Mouse+Gamer+RGB', description: 'Diseño ergonómico y precisión láser para el gaming.' },
    { id: 3, title: 'Teclado Mecánico 60%', price: 120.00, image: 'https://via.placeholder.com/400x200?text=Teclado+Mecanico', description: 'Compacto y con switches táctiles de respuesta rápida.' },
    { id: 4, title: 'Webcam HD 1080p', price: 35.75, image: 'https://via.placeholder.com/400x200?text=Webcam+HD', description: 'Ideal para videollamadas y streaming con calidad Full HD.' },
];

/**
 * 7. Fetch API: Consumir datos (Simulado) y Renderizar Productos
 */
const fetchProducts = async () => {
    // En un proyecto real, se usaría: const response = await fetch(API_URL);
    // Para esta demo, usamos los datos de mock para una experiencia de producto completa.
    
    try {
        // En el proyecto real: const data = await response.json();
        // Usamos los datos simulados:
        const products = mockProducts; 
        renderProducts(products);
    } catch (error) {
        console.error('Error al obtener los productos:', error);
        productsContainer.innerHTML = '<p class="text-danger text-center">Error al cargar los productos. Intenta de nuevo más tarde.</p>';
    }
};

/**
 * Renderiza los productos en el DOM en forma de tarjetas (cards) usando Flexbox (columnas de Bootstrap).
 * @param {Array} products - Lista de objetos de producto.
 */
const renderProducts = (products) => {
    productsContainer.innerHTML = ''; // Limpiar el contenedor
    products.forEach(product => {
        const productCard = document.createElement('div');
        // Clases de Bootstrap para un diseño responsivo con Flexbox
        productCard.className = 'col-lg-3 col-md-4 col-sm-6'; 
        
        productCard.innerHTML = `
            <div class="card h-100 shadow-sm">
                <img src="${product.image}" class="card-img-top product-card-img" alt="${product.title}">
                <div class="card-body d-flex flex-column">
                    <h5 class="card-title">${product.title}</h5>
                    <p class="card-text">${product.description.substring(0, 50)}...</p>
                    <p class="fs-4 fw-bold mt-auto">$${product.price.toFixed(2)}</p>
                    <button class="btn btn-primary add-to-cart-btn mt-2" data-product-id="${product.id}">
                        <i class="fas fa-cart-plus"></i> Añadir al Carrito
                    </button>
                </div>
            </div>
        `;
        productsContainer.appendChild(productCard);
    });

    // Añadir event listeners a los botones "Añadir al Carrito"
    document.querySelectorAll('.add-to-cart-btn').forEach(button => {
        button.addEventListener('click', (e) => {
            const productId = parseInt(e.target.dataset.productId);
            const product = mockProducts.find(p => p.id === productId);
            if (product) {
                addToCart(product);
            }
        });
    });
};

// --- 8. Carrito de Compras Dinámico (LocalStorage) ---

/**
 * 8.1 Agregar Producto al Carrito
 * @param {Object} product - El producto a añadir.
 */
const addToCart = (product) => {
    const existingItem = cart.find(item => item.id === product.id);

    if (existingItem) {
        existingItem.quantity += 1; // Editar Cantidad
    } else {
        cart.push({
            id: product.id,
            title: product.title,
            price: product.price,
            quantity: 1
        });
    }

    updateCart(); // Actualizar el carrito en la interfaz y LocalStorage
    showToast(`${product.title} añadido al carrito.`);
};

/**
 * Actualiza la vista del carrito, el contador y guarda en localStorage.
 */
const updateCart = () => {
    // 8.2 Uso de localStorage
    localStorage.setItem('ecommerceCart', JSON.stringify(cart)); 
    
    // 8.3 Contador Dinámico
    const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
    cartCounter.textContent = totalItems;

    // 9. Visualización, Edición y Total Dinámico
    renderCartItems();
};

// --- 9. Edición y Visualización del Carrito ---

/**
 * 9.1 Visualización de Productos en el Carrito y 9.3 Total Dinámico.
 */
const renderCartItems = () => {
    cartItemsList.innerHTML = '';
    let total = 0;

    if (cart.length === 0) {
        emptyCartMessage.classList.remove('d-none');
    } else {
        emptyCartMessage.classList.add('d-none');
        
        cart.forEach(item => {
            const itemTotal = item.price * item.quantity;
            total += itemTotal;
            
            const listItem = document.createElement('div');
            // Usando clases de list-group y flex para la visualización
            listItem.className = 'list-group-item d-flex justify-content-between align-items-center';
            listItem.innerHTML = `
                <div class="d-flex align-items-center">
                    <h6 class="mb-0 me-3">${item.title}</h6>
                    <span class="badge bg-info text-dark me-2">$${item.price.toFixed(2)}</span>
                </div>
                <div class="d-flex align-items-center">
                    <button class="btn btn-sm btn-outline-secondary decrease-quantity" data-id="${item.id}">-</button>
                    <span class="mx-2">${item.quantity}</span>
                    <button class="btn btn-sm btn-outline-secondary increase-quantity" data-id="${item.id}">+</button>
                    
                    <span class="ms-3 fw-bold">$${itemTotal.toFixed(2)}</span>
                    
                    <button class="btn btn-danger btn-sm ms-3 remove-item" data-id="${item.id}">
                        <i class="fas fa-trash"></i>
                    </button>
                </div>
            `;
            cartItemsList.appendChild(listItem);
        });

        // Añadir Event Listeners para edición/eliminación
        document.querySelectorAll('.increase-quantity').forEach(btn => {
            btn.addEventListener('click', (e) => changeQuantity(parseInt(e.currentTarget.dataset.id), 1));
        });
        document.querySelectorAll('.decrease-quantity').forEach(btn => {
            btn.addEventListener('click', (e) => changeQuantity(parseInt(e.currentTarget.dataset.id), -1));
        });
        document.querySelectorAll('.remove-item').forEach(btn => {
            btn.addEventListener('click', (e) => removeItem(parseInt(e.currentTarget.dataset.id)));
        });
    }

    cartTotalElement.textContent = total.toFixed(2);
};

/**
 * 9.2 Modifica la cantidad de un producto en el carrito.
 * @param {number} id - ID del producto.
 * @param {number} delta - Cantidad a sumar (1 o -1).
 */
const changeQuantity = (id, delta) => {
    const item = cart.find(item => item.id === id);
    if (item) {
        item.quantity += delta;
        
        // Si la cantidad llega a 0 o menos, eliminar el producto
        if (item.quantity <= 0) {
            removeItem(id);
        } else {
            updateCart();
        }
    }
};

/**
 * 9.2 Elimina un producto del carrito.
 * @param {number} id - ID del producto a eliminar.
 */
const removeItem = (id) => {
    cart = cart.filter(item => item.id !== id);
    updateCart();
    showToast('Producto eliminado del carrito.', 'danger');
};

/**
 * Utilidad para mostrar notificaciones al usuario.
 * @param {string} message - Mensaje a mostrar.
 * @param {string} type - Clase de Bootstrap (e.g., 'success', 'danger', 'primary').
 */
const showToast = (message, type = 'success') => {
    // Usamos el Toast de Bootstrap (necesitas definir el HTML del Toast en index.html)
    // Para simplificar, usaremos un alert temporal.
    const alertDiv = document.createElement('div');
    alertDiv.className = `alert alert-${type} position-fixed top-0 start-50 translate-middle-x mt-3`;
    alertDiv.setAttribute('role', 'alert');
    alertDiv.textContent = message;
    
    document.body.appendChild(alertDiv);
    
    setTimeout(() => {
        alertDiv.remove();
    }, 2500);
};

// --- 7. DOM: Validación de Formulario (Email y Requeridos) ---

/**
 * Valida el formato del correo electrónico.
 * @param {string} email - Correo electrónico a validar.
 * @returns {boolean} True si el formato es válido.
 */
const validateEmail = (email) => {
    const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return re.test(String(email).toLowerCase());
};

contactForm.addEventListener('submit', function(e) {
    e.preventDefault();
    let formIsValid = true;

    // 1. Validar campos requeridos y mostrar feedback
    this.querySelectorAll('input[required], textarea[required]').forEach(input => {
        if (!input.value.trim()) {
            input.classList.add('is-invalid');
            formIsValid = false;
        } else {
            input.classList.remove('is-invalid');
        }
    });

    // 2. Validación de formato de Email
    if (!validateEmail(emailInput.value.trim())) {
        emailInput.classList.add('is-invalid');
        document.getElementById('email-feedback').textContent = 'Por favor, ingresa un correo electrónico válido.';
        formIsValid = false;
    } else {
        emailInput.classList.remove('is-invalid');
    }

    if (formIsValid) {
        // Enviar datos con Fetch (para Formspree)
        const formStatus = document.getElementById('form-status');
        formStatus.classList.remove('d-none', 'text-danger');
        formStatus.classList.add('text-primary');
        formStatus.textContent = 'Enviando...';

        fetch(this.action, {
            method: this.method,
            body: new FormData(this),
            headers: {
                'Accept': 'application/json'
            }
        }).then(response => {
            if (response.ok) {
                formStatus.textContent = '¡Gracias por contactarnos! Tu mensaje ha sido enviado.';
                formStatus.classList.remove('text-primary');
                formStatus.classList.add('text-success');
                this.reset();
            } else {
                formStatus.textContent = 'Ocurrió un error al enviar el mensaje.';
                formStatus.classList.remove('text-primary');
                formStatus.classList.add('text-danger');
            }
        }).catch(error => {
            console.error('Fetch Error:', error);
            formStatus.textContent = 'Error de conexión. Intenta de nuevo.';
            formStatus.classList.remove('text-primary');
            formStatus.classList.add('text-danger');
        });
    }
});

// --- Inicialización ---
document.addEventListener('DOMContentLoaded', () => {
    fetchProducts(); // Cargar productos al inicio
    updateCart();    // Cargar estado del carrito
    
    // Evento para el botón de Pagar (simulación)
    document.getElementById('checkout-button').addEventListener('click', () => {
        if (cart.length > 0) {
            alert(`Procesando pago por un total de $${cartTotalElement.textContent}. Gracias por tu compra.`);
            cart = []; // Vaciar carrito
            updateCart();
            // Cerrar el modal (se requiere la instancia de Bootstrap, pero alert simple funciona para el ejemplo)
            const modalElement = document.getElementById('cartModal');
            const modal = bootstrap.Modal.getInstance(modalElement);
            if(modal) modal.hide();
        } else {
            alert('El carrito está vacío. Añade productos para pagar.');
        }
    });
});

