# WIREFRAMES - PLATAFORMA MOTHERNATURE
## Diseño UX/UI para E-commerce de Productos Naturales

**Fecha:** 05 de Septiembre, 2025  
**Versión:** 1.0  
**Diseño:** Equipo UX/UI Cascade  

---

## 🎨 IDENTIDAD VISUAL MOTHERNATURE

### Paleta de Colores Principal
```css
/* Colores Primarios - Naturaleza Vibrante */
--nature-green: #4CAF50      /* Verde principal */
--forest-green: #2E7D32     /* Verde oscuro */
--leaf-green: #8BC34A       /* Verde claro */
--sunshine-yellow: #FFC107   /* Amarillo energético */
--earth-brown: #8D6E63      /* Marrón tierra */

/* Colores Secundarios - Juventud y Energía */
--vibrant-orange: #FF9800    /* Naranja vibrante */
--fresh-blue: #03DAC6       /* Azul fresco */
--berry-purple: #9C27B0     /* Morado natural */
--coral-pink: #FF7043       /* Rosa coral */

/* Colores Neutros */
--pure-white: #FFFFFF       /* Blanco puro */
--soft-gray: #F5F5F5        /* Gris suave */
--text-dark: #212121        /* Texto principal */
--text-light: #757575       /* Texto secundario */
```

### Tipografía
```css
/* Fuente Principal - Moderna y Amigable */
font-family: 'Inter', 'Poppins', sans-serif;

/* Jerarquía Tipográfica */
.heading-xl: 48px, bold, line-height: 1.2
.heading-lg: 36px, bold, line-height: 1.3
.heading-md: 24px, semibold, line-height: 1.4
.heading-sm: 18px, semibold, line-height: 1.5
.body-lg: 16px, regular, line-height: 1.6
.body-md: 14px, regular, line-height: 1.6
.body-sm: 12px, regular, line-height: 1.5
```

---

## 📱 WIREFRAMES PRINCIPALES

### 1. PÁGINA DE INICIO (HOME)

```
┌─────────────────────────────────────────────────────────────┐
│ [🌿 LOGO] MotherNature    [🔍] [🛒] [👤] [☰]              │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  🌱 HERO SECTION - Imagen vibrante de productos naturales  │
│     "Descubre el Poder de la Naturaleza"                   │
│     [Explorar Productos] [Ver Recetas]                     │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ 🏷️ CATEGORÍAS DESTACADAS                                   │
│ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐           │
│ │🥬 Frescos│ │🌾 Granos│ │🍯 Miel  │ │🧴 Bebidas│          │
│ │ Mumbai  │ │Pan India│ │Pan India│ │Pan India│           │
│ └─────────┘ └─────────┘ └─────────┘ └─────────┘           │
├─────────────────────────────────────────────────────────────┤
│ ⭐ PRODUCTOS DESTACADOS                                     │
│ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│ │ [IMG] Prod1 │ │ [IMG] Prod2 │ │ [IMG] Prod3 │           │
│ │ ₹299 ₹199   │ │ ₹450 ₹350   │ │ ₹180 ₹150   │           │
│ │ ⭐4.8 (234) │ │ ⭐4.9 (156) │ │ ⭐4.7 (89)  │           │
│ │ [Agregar]   │ │ [Agregar]   │ │ [Agregar]   │           │
│ └─────────────┘ └─────────────┘ └─────────────┘           │
├─────────────────────────────────────────────────────────────┤
│ 📚 CONTENIDO EDUCATIVO                                      │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ 🥗 "5 Recetas Saludables para el Desayuno"             │ │
│ │ 📖 "Beneficios de los Superalimentos"                  │ │
│ │ 🎥 "Cómo elegir productos orgánicos"                   │ │
│ └─────────────────────────────────────────────────────────┘ │
├─────────────────────────────────────────────────────────────┤
│ 💬 CHAT WHATSAPP FLOTANTE                                   │
│ 📧 NEWSLETTER: "Únete a la familia MotherNature"           │
│ 🌿 FOOTER: Enlaces, Contacto, Redes Sociales               │
└─────────────────────────────────────────────────────────────┘
```

### 2. CATÁLOGO DE PRODUCTOS

```
┌─────────────────────────────────────────────────────────────┐
│ [🌿] MotherNature > Productos                               │
├─────────────────────────────────────────────────────────────┤
│ 🔍 [Buscar productos naturales...]                         │
│                                                             │
│ FILTROS:                           ORDENAR POR:             │
│ ☐ Perecederos (Mumbai)            [Más Popular ▼]          │
│ ☐ No Perecederos (Pan India)                               │
│ ☐ Orgánicos Certificados         📍 Tu ubicación: Mumbai   │
│ ☐ Sin Gluten                                               │
│ ☐ Vegano                          🚚 Entrega: Hoy          │
│                                                             │
│ Precio: [₹0] ────●──── [₹2000]                            │
├─────────────────────────────────────────────────────────────┤
│ PRODUCTOS (Grid 3x3)                                       │
│ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│ │🥬 [IMG]     │ │🌾 [IMG]     │ │🍯 [IMG]     │           │
│ │Espinacas    │ │Quinoa       │ │Miel Pura    │           │
│ │Orgánicas    │ │Boliviana    │ │Himalaya     │           │
│ │₹89 ₹69      │ │₹450 ₹399    │ │₹280 ₹249    │           │
│ │⭐4.8 🚚Hoy   │ │⭐4.9 🚚3 días│ │⭐4.7 🚚2 días│          │
│ │[+ Carrito]  │ │[+ Carrito]  │ │[+ Carrito]  │           │
│ └─────────────┘ └─────────────┘ └─────────────┘           │
│                                                             │
│ [Cargar más productos...]                                   │
├─────────────────────────────────────────────────────────────┤
│ 🛒 CARRITO FLOTANTE: 3 items - ₹567                       │
└─────────────────────────────────────────────────────────────┘
```

### 3. PÁGINA DE PRODUCTO INDIVIDUAL

```
┌─────────────────────────────────────────────────────────────┐
│ [🌿] MotherNature > Productos > Miel Orgánica              │
├─────────────────────────────────────────────────────────────┤
│ ┌─────────────────┐  MIEL ORGÁNICA HIMALAYA                │
│ │                 │  ⭐⭐⭐⭐⭐ 4.8 (234 reseñas)           │
│ │   [IMG GRANDE]  │                                         │
│ │                 │  ₹280 ₹249 (11% OFF)                   │
│ │                 │  🚚 Entrega en 2-3 días                │
│ │ [◀] [IMG] [▶]   │  📍 Disponible Pan India                │
│ └─────────────────┘                                         │
│                     CANTIDAD: [- 1 +]  [AGREGAR AL CARRITO]│
│                     💚 [LISTA DE DESEOS]                    │
├─────────────────────────────────────────────────────────────┤
│ 📋 DESCRIPCIÓN                                              │
│ "Miel pura y orgánica cosechada en las montañas del        │
│ Himalaya. Rica en antioxidantes y propiedades curativas."  │
│                                                             │
│ 🌿 BENEFICIOS:                                              │
│ • Fortalece el sistema inmunológico                        │
│ • Propiedades antibacterianas naturales                    │
│ • Rica en vitaminas y minerales                            │
│                                                             │
│ 📊 INFORMACIÓN NUTRICIONAL:                                 │
│ Calorías: 304 por 100g | Carbohidratos: 82g               │
├─────────────────────────────────────────────────────────────┤
│ 💬 RESEÑAS DE CLIENTES                                      │
│ ⭐⭐⭐⭐⭐ "Excelente calidad, muy recomendada" - Priya      │
│ ⭐⭐⭐⭐⭐ "Sabor auténtico, llegó muy bien empacada" - Raj  │
│                                                             │
│ 🔗 PRODUCTOS RELACIONADOS                                   │
│ [Miel de Acacia] [Miel con Jengibre] [Miel de Flores]     │
└─────────────────────────────────────────────────────────────┘
```

### 4. CARRITO DE COMPRAS

```
┌─────────────────────────────────────────────────────────────┐
│ [🌿] MotherNature > Carrito                                 │
├─────────────────────────────────────────────────────────────┤
│ 🛒 TU CARRITO (3 productos)                                │
│                                                             │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ [IMG] Espinacas Orgánicas    [- 2 +]    ₹69 x 2 = ₹138│ │
│ │ 🚚 Entrega hoy (Perecedero - Mumbai)            [🗑️]   │ │
│ └─────────────────────────────────────────────────────────┘ │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ [IMG] Quinoa Boliviana       [- 1 +]    ₹399 x 1 = ₹399│ │
│ │ 🚚 Entrega en 3 días (Pan India)                [🗑️]   │ │
│ └─────────────────────────────────────────────────────────┘ │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ [IMG] Miel Himalaya          [- 1 +]    ₹249 x 1 = ₹249│ │
│ │ 🚚 Entrega en 2 días (Pan India)                [🗑️]   │ │
│ └─────────────────────────────────────────────────────────┘ │
│                                                             │
│ 🎟️ CUPÓN DE DESCUENTO                                      │
│ [Ingresa código] [APLICAR]                                  │
│                                                             │
│ 💰 RESUMEN DEL PEDIDO                                       │
│ Subtotal:                                          ₹786     │
│ Descuento:                                        -₹50      │
│ Envío:                                            ₹40       │
│ ─────────────────────────────────────────────────────────   │
│ TOTAL:                                            ₹776      │
│                                                             │
│ [CONTINUAR COMPRANDO]              [PROCEDER AL PAGO]       │
└─────────────────────────────────────────────────────────────┘
```

### 5. CHECKOUT Y AUTENTICACIÓN OTP

```
┌─────────────────────────────────────────────────────────────┐
│ [🌿] MotherNature > Checkout                                │
├─────────────────────────────────────────────────────────────┤
│ 📱 AUTENTICACIÓN REQUERIDA                                  │
│                                                             │
│ Para completar tu pedido, necesitas registrarte:           │
│                                                             │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ 📞 NÚMERO DE TELÉFONO                                   │ │
│ │ +91 [__________]                                        │ │
│ │                                                         │ │
│ │ 📧 EMAIL (Opcional)                                     │ │
│ │ [________________________]                             │ │
│ │                                                         │ │
│ │ 👤 NOMBRE COMPLETO                                      │ │
│ │ [________________________]                             │ │
│ │                                                         │ │
│ │              [ENVIAR OTP]                               │ │
│ └─────────────────────────────────────────────────────────┘ │
│                                                             │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ 🔐 VERIFICACIÓN OTP                                     │ │
│ │ Ingresa el código enviado a +91 98765xxxxx:            │ │
│ │                                                         │ │
│ │ [_] [_] [_] [_] [_] [_]                                 │ │
│ │                                                         │ │
│ │ ¿No recibiste el código? [Reenviar OTP]                │ │
│ │                                                         │ │
│ │              [VERIFICAR]                                │ │
│ └─────────────────────────────────────────────────────────┘ │
├─────────────────────────────────────────────────────────────┤
│ 🏠 DIRECCIÓN DE ENTREGA                                     │
│ [Dirección completa...]                                     │
│                                                             │
│ 💳 MÉTODO DE PAGO                                           │
│ ○ UPI  ○ Tarjeta  ○ Wallet  ○ COD                         │
│                                                             │
│ Total: ₹776                        [REALIZAR PEDIDO]       │
└─────────────────────────────────────────────────────────────┘
```

### 6. PERFIL DE USUARIO Y LOYALTY

```
┌─────────────────────────────────────────────────────────────┐
│ [🌿] MotherNature > Mi Perfil                               │
├─────────────────────────────────────────────────────────────┤
│ 👤 HOLA, PRIYA SHARMA                                       │
│ 📞 +91 98765xxxxx  📧 priya@email.com                      │
│                                                             │
│ ⭐ PUNTOS MOTHERNATURE: 1,250 puntos                        │
│ 🎁 Próxima recompensa en 250 puntos                        │
│ [Ver Recompensas Disponibles]                               │
├─────────────────────────────────────────────────────────────┤
│ 📋 MIS PEDIDOS                                              │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ #MN001234 - ₹776 - Entregado ✅                         │ │
│ │ 3 productos • 15 Sep 2025                               │ │
│ │ [Ver Detalles] [Reordenar] [Calificar]                 │ │
│ └─────────────────────────────────────────────────────────┘ │
│                                                             │
│ 💚 LISTA DE DESEOS (5 productos)                           │
│ [Miel con Jengibre] [Aceite de Coco] [Té Verde]...        │
│                                                             │
│ 🏠 MIS DIRECCIONES                                          │
│ 📍 Casa: Bandra West, Mumbai - 400050                      │
│ 🏢 Oficina: Andheri East, Mumbai - 400069                  │
│ [+ Agregar Nueva Dirección]                                │
│                                                             │
│ 🎯 CHALLENGES ACTIVOS                                       │
│ 🥗 "Compra 5 productos orgánicos" - 3/5 ✓                 │
│ 🌱 "Prueba 3 recetas nuevas" - 1/3 ✓                      │
├─────────────────────────────────────────────────────────────┤
│ ⚙️ CONFIGURACIÓN                                            │
│ 🔔 Notificaciones  📧 Email Marketing  🌐 Idioma           │
└─────────────────────────────────────────────────────────────┘
```

### 7. CONTENIDO EDUCATIVO (RECETAS/BLOG)

```
┌─────────────────────────────────────────────────────────────┐
│ [🌿] MotherNature > Recetas Saludables                     │
├─────────────────────────────────────────────────────────────┤
│ 🔍 [Buscar recetas...]                                      │
│                                                             │
│ CATEGORÍAS: [Desayuno] [Almuerzo] [Cena] [Snacks] [Bebidas]│
│ FILTROS: [Vegano] [Sin Gluten] [Keto] [Fácil] [Rápido]    │
├─────────────────────────────────────────────────────────────┤
│ 🌟 RECETA DESTACADA                                         │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ [IMG GRANDE] Smoothie Verde Energizante                 │ │
│ │ ⭐4.9 • 15 min • Fácil • Vegano                         │ │
│ │ "Perfecto para comenzar el día con energía natural"    │ │
│ │ [Ver Receta Completa]                                   │ │
│ └─────────────────────────────────────────────────────────┘ │
│                                                             │
│ 📚 TODAS LAS RECETAS                                        │
│ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│ │ [IMG] Bowl  │ │ [IMG] Sopa  │ │ [IMG] Té    │           │
│ │ Acai Casero │ │ Detox Verde │ │ Jengibre    │           │
│ │ ⭐4.8 20min  │ │ ⭐4.7 30min  │ │ ⭐4.9 10min  │           │
│ │ [Ver Más]   │ │ [Ver Más]   │ │ [Ver Más]   │           │
│ └─────────────┘ └─────────────┘ └─────────────┘           │
├─────────────────────────────────────────────────────────────┤
│ 📖 ARTÍCULOS EDUCATIVOS                                     │
│ • "10 Superalimentos que debes incluir en tu dieta"        │
│ • "Cómo leer etiquetas de productos orgánicos"             │
│ • "Beneficios de una alimentación consciente"              │
│                                                             │
│ 🎥 VIDEOS EDUCATIVOS                                        │
│ • "Cómo preparar leches vegetales en casa"                 │
│ • "Guía completa de especias ayurvédicas"                  │
└─────────────────────────────────────────────────────────────┘
```
