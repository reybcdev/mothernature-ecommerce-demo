# INFORME TÉCNICO - PLATAFORMA MOTHERNATURE (PARTE 2)
## Arquitectura Técnica y Tecnologías

---

## 🏗️ ARQUITECTURA Y TECNOLOGÍAS RECOMENDADAS

### Stack Tecnológico Principal

#### Frontend
- **Next.js 14** (App Router) - Framework React con SSR/SSG para SEO óptimo
- **TypeScript** - Type safety y mejor experiencia de desarrollo
- **Tailwind CSS** - Framework CSS utilitario para diseño rápido
- **Framer Motion** - Animaciones fluidas para UI vibrante
- **React Query/TanStack Query** - State management y caching
- **Zustand** - State management ligero y eficiente

#### Backend
- **Node.js + Express.js** - API REST escalable
- **TypeScript** - Consistencia con frontend
- **Prisma ORM** - Database management y migrations
- **PostgreSQL** - Base de datos principal relacional
- **Redis** - Caching, sessions y real-time data
- **Socket.io** - Notificaciones en tiempo real

#### Infraestructura
- **Vercel/Netlify** - Deployment de frontend
- **Railway/DigitalOcean** - Hosting de backend
- **AWS S3/Cloudinary** - Almacenamiento de media
- **MongoDB** - Analytics y logs no estructurados
- **Docker** - Containerización para consistencia

---

## 📁 ESTRUCTURA DEL PROYECTO

### Arquitectura de Microservicios

```
mothernature-platform/
├── apps/
│   ├── web/                    # Next.js Frontend
│   │   ├── src/
│   │   │   ├── app/           # App Router pages
│   │   │   ├── components/    # UI Components
│   │   │   ├── hooks/         # Custom hooks
│   │   │   ├── lib/           # Utilities
│   │   │   └── styles/        # Global styles
│   │   ├── public/            # Static assets
│   │   └── package.json
│   │
│   ├── api/                    # Express.js Backend
│   │   ├── src/
│   │   │   ├── routes/        # API endpoints
│   │   │   ├── controllers/   # Business logic
│   │   │   ├── middleware/    # Auth, validation
│   │   │   ├── services/      # External integrations
│   │   │   └── utils/         # Helper functions
│   │   └── package.json
│   │
│   ├── admin/                  # Admin Dashboard
│   └── mobile/                 # Future React Native App
│
├── packages/
│   ├── ui/                     # Shared UI Components
│   ├── database/               # Prisma Schema & Migrations
│   ├── auth/                   # Authentication Logic
│   ├── payments/               # Payment Integrations
│   ├── notifications/          # Email/SMS/Push Services
│   └── analytics/              # Tracking & Analytics
│
├── services/
│   ├── inventory/              # Product Management
│   ├── orders/                 # Order Processing
│   ├── delivery/               # Logistics Integration
│   ├── content/                # CMS for Recipes/Blogs
│   └── marketing/              # Email Campaigns & Loyalty
│
└── infrastructure/
    ├── docker/                 # Container Configurations
    ├── k8s/                    # Kubernetes Manifests
    └── terraform/              # Infrastructure as Code
```

---

## 🗄️ DISEÑO DE BASE DE DATOS

### Schema Principal (PostgreSQL)

```sql
-- Users & Authentication
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    phone VARCHAR(15) UNIQUE NOT NULL,
    email VARCHAR(255),
    name VARCHAR(255),
    is_verified BOOLEAN DEFAULT FALSE,
    loyalty_points INTEGER DEFAULT 0,
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

-- Categories
CREATE TABLE categories (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(255) NOT NULL,
    slug VARCHAR(255) UNIQUE NOT NULL,
    description TEXT,
    image_url VARCHAR(500),
    parent_id UUID REFERENCES categories(id),
    is_active BOOLEAN DEFAULT TRUE
);

-- Products & Inventory
CREATE TABLE products (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(255) NOT NULL,
    slug VARCHAR(255) UNIQUE NOT NULL,
    description TEXT,
    category_id UUID REFERENCES categories(id),
    is_perishable BOOLEAN DEFAULT FALSE,
    availability_zone ENUM('mumbai', 'pan_india') DEFAULT 'pan_india',
    price DECIMAL(10,2) NOT NULL,
    mrp DECIMAL(10,2),
    stock_quantity INTEGER DEFAULT 0,
    min_order_quantity INTEGER DEFAULT 1,
    images JSONB,
    nutritional_info JSONB,
    benefits TEXT[],
    ingredients TEXT[],
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

-- Orders & Payments
CREATE TABLE orders (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    order_number VARCHAR(50) UNIQUE NOT NULL,
    user_id UUID REFERENCES users(id),
    total_amount DECIMAL(10,2) NOT NULL,
    discount_amount DECIMAL(10,2) DEFAULT 0,
    delivery_fee DECIMAL(10,2) DEFAULT 0,
    tax_amount DECIMAL(10,2) DEFAULT 0,
    final_amount DECIMAL(10,2) NOT NULL,
    payment_status ENUM('pending', 'completed', 'failed', 'refunded') DEFAULT 'pending',
    delivery_status ENUM('pending', 'confirmed', 'packed', 'shipped', 'delivered', 'cancelled') DEFAULT 'pending',
    razorpay_order_id VARCHAR(255),
    razorpay_payment_id VARCHAR(255),
    delivery_address JSONB NOT NULL,
    delivery_partner VARCHAR(100),
    tracking_id VARCHAR(255),
    estimated_delivery TIMESTAMP,
    delivered_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

-- Order Items
CREATE TABLE order_items (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    order_id UUID REFERENCES orders(id) ON DELETE CASCADE,
    product_id UUID REFERENCES products(id),
    quantity INTEGER NOT NULL,
    unit_price DECIMAL(10,2) NOT NULL,
    total_price DECIMAL(10,2) NOT NULL,
    product_snapshot JSONB -- Store product details at time of order
);

-- Visitor Tracking
CREATE TABLE visitor_sessions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    session_id VARCHAR(255) UNIQUE NOT NULL,
    ip_address INET,
    user_agent TEXT,
    referrer VARCHAR(500),
    location_data JSONB,
    pages_visited JSONB DEFAULT '[]',
    time_spent INTEGER DEFAULT 0,
    converted BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

-- Coupons & Offers
CREATE TABLE coupons (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    code VARCHAR(50) UNIQUE NOT NULL,
    title VARCHAR(255) NOT NULL,
    description TEXT,
    discount_type ENUM('percentage', 'fixed', 'free_shipping') NOT NULL,
    discount_value DECIMAL(10,2) NOT NULL,
    min_order_amount DECIMAL(10,2),
    max_discount_amount DECIMAL(10,2),
    usage_limit INTEGER,
    used_count INTEGER DEFAULT 0,
    valid_from TIMESTAMP NOT NULL,
    valid_until TIMESTAMP NOT NULL,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT NOW()
);

-- Content Management
CREATE TABLE content_posts (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    title VARCHAR(255) NOT NULL,
    slug VARCHAR(255) UNIQUE NOT NULL,
    content TEXT NOT NULL,
    excerpt TEXT,
    featured_image VARCHAR(500),
    post_type ENUM('recipe', 'blog', 'education', 'news') NOT NULL,
    status ENUM('draft', 'published', 'archived') DEFAULT 'draft',
    tags TEXT[],
    meta_description VARCHAR(160),
    author_id UUID REFERENCES users(id),
    published_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

-- Loyalty Program
CREATE TABLE loyalty_transactions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id),
    transaction_type ENUM('earned', 'redeemed', 'expired') NOT NULL,
    points INTEGER NOT NULL,
    description VARCHAR(255),
    order_id UUID REFERENCES orders(id),
    expires_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT NOW()
);
```

---

## 🔗 INTEGRACIONES DE TERCEROS

### 1. Autenticación OTP

#### Twilio Integration
```javascript
const twilioClient = require('twilio')(
    process.env.TWILIO_ACCOUNT_SID,
    process.env.TWILIO_AUTH_TOKEN
);

const sendOTP = async (phoneNumber) => {
    return await twilioClient.verify.v2
        .services(process.env.TWILIO_VERIFY_SERVICE_SID)
        .verifications
        .create({
            to: `+91${phoneNumber}`,
            channel: 'sms'
        });
};

const verifyOTP = async (phoneNumber, code) => {
    return await twilioClient.verify.v2
        .services(process.env.TWILIO_VERIFY_SERVICE_SID)
        .verificationChecks
        .create({
            to: `+91${phoneNumber}`,
            code: code
        });
};
```

#### MSG91 Alternative
```javascript
const msg91 = require('msg91')(process.env.MSG91_AUTH_KEY);

const sendOTPMsg91 = async (phoneNumber) => {
    return await msg91.send({
        sender: 'MTNATURE',
        route: '4',
        country: '91',
        sms: [{
            message: `Your MotherNature OTP is: {{otp}}. Valid for 10 minutes.`,
            to: [phoneNumber]
        }]
    });
};
```

### 2. Pagos - Razorpay

```javascript
const Razorpay = require('razorpay');

const razorpay = new Razorpay({
    key_id: process.env.RAZORPAY_KEY_ID,
    key_secret: process.env.RAZORPAY_KEY_SECRET
});

// Create Order
const createRazorpayOrder = async (orderData) => {
    const options = {
        amount: orderData.amount * 100, // amount in paisa
        currency: 'INR',
        receipt: orderData.orderId,
        notes: {
            user_id: orderData.userId,
            order_type: orderData.isPerishable ? 'perishable' : 'non_perishable'
        }
    };
    
    return await razorpay.orders.create(options);
};

// Webhook Handler
app.post('/webhooks/razorpay', (req, res) => {
    const signature = req.headers['x-razorpay-signature'];
    const body = JSON.stringify(req.body);
    
    const expectedSignature = crypto
        .createHmac('sha256', process.env.RAZORPAY_WEBHOOK_SECRET)
        .update(body)
        .digest('hex');
    
    if (signature === expectedSignature) {
        handlePaymentWebhook(req.body);
        res.status(200).send('OK');
    } else {
        res.status(400).send('Invalid signature');
    }
});
```

### 3. Delivery Partners Integration

```javascript
// Multi-partner delivery abstraction
class DeliveryService {
    constructor() {
        this.partners = {
            dunzo: new DunzoAPI(process.env.DUNZO_API_KEY),
            shadowfax: new ShadowfaxAPI(process.env.SHADOWFAX_API_KEY),
            delhivery: new DelhiveryAPI(process.env.DELHIVERY_API_KEY)
        };
    }
    
    async createDelivery(orderData) {
        const partner = this.selectOptimalPartner(orderData);
        
        switch(partner) {
            case 'dunzo':
                return await this.createDunzoDelivery(orderData);
            case 'shadowfax':
                return await this.createShadowfaxShipment(orderData);
            case 'delhivery':
                return await this.createDelhiveryOrder(orderData);
            default:
                throw new Error('No suitable delivery partner found');
        }
    }
    
    selectOptimalPartner(orderData) {
        // Priority logic based on location, product type, cost
        if (orderData.isPerishable && orderData.city === 'mumbai') {
            return 'dunzo'; // Hyperlocal for perishables in Mumbai
        }
        
        if (orderData.weight > 5 && !orderData.isPerishable) {
            return 'delhivery'; // Heavy items pan-India
        }
        
        return 'shadowfax'; // Default for pan-India
    }
    
    async createDunzoDelivery(orderData) {
        return await this.partners.dunzo.createTask({
            task_type: 'delivery',
            pickup_location: orderData.pickupAddress,
            drop_location: orderData.deliveryAddress,
            package_details: {
                weight: orderData.weight,
                dimensions: orderData.dimensions,
                fragile: orderData.isPerishable
            }
        });
    }
}
```
