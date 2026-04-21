# Digitic Admin Dashboard

## 1. Project Overview

The **Digitic Admin Dashboard** is a comprehensive management interface for e-commerce administrators. It provides full control over products, orders, customers, blogs, coupons, and system configurations.

**Target Users:** Administrators, Store Managers, Content Editors

---

## 2. Tech Stack

| Category         | Technology                     |
| ------------------| --------------------------------|
| Framework        | React 18.3                     |
| Build Tool       | Vite 5.3                       |
| State Management | Redux Toolkit                  |
| UI Library       | Ant Design 5.19                |
| Styling          | Bootstrap 5.3, CSS             |
| Routing          | React Router DOM 6.24          |
| Forms            | Formik + Yup                   |
| HTTP Client      | Axios                          |
| Charts           | @ant-design/charts             |
| Icons            | @ant-design/icons, react-icons |
| Rich Text        | React Quill                    |
| Notifications    | React Toastify                 |
| File Upload      | React Dropzone                 |

---

## 3. Features

### Authentication & Security

- JWT-based admin login with role verification
- Protected routes via `PrivateRoutes` component
- Token refresh mechanism

### Dashboard

- Sales analytics with charts (monthly/annual data)
- Order statistics visualization
- Quick access to management sections

### Product Management

- Add/Edit products with image uploads
- Product listing with search/filter
- Category, brand, and color associations

### Order Management

- View all customer orders
- Update order status
- Order details and history

### Content Management

- Blog creation and editing (rich text)
- Blog categories management
- Brand and color configuration

### Customer Management

- View registered customers
- Block/Unblock user accounts

### Coupon System

- Create discount coupons
- Manage coupon codes and validity

### Enquiries

- View customer contact form submissions
- Mark enquiries as resolved

---

## 4. Project Structure

```
admin/
├── src/
│   ├── app/               # Store configuration
│   ├── assets/            # Static assets
│   ├── components/        # Shared UI components
│   │   ├── CustomEditor.jsx
│   │   ├── MainLayout.jsx
│   │   └── CustomInput.jsx
│   ├── features/          # Redux slices (by domain)
│   │   ├── auth/          # Authentication state
│   │   ├── product/       # Products CRUD
│   │   ├── blogs/         # Blog management
│   │   ├── brand/         # Brand management
│   │   ├── color/         # Color management
│   │   ├── coupon/        # Coupon management
│   │   ├── pcategory/     # Product categories
│   │   ├── bcategory/     # Blog categories
│   │   ├── enquiry/       # Customer enquiries
│   │   ├── cutomers/      # Customer management
│   │   └── upload/        # File upload handling
│   ├── pages/             # Route-level components
│   │   ├── Dashboard.jsx
│   │   ├── Login.jsx
│   │   ├── Addproduct.jsx
│   │   ├── Productlist.jsx
│   │   ├── Orders.jsx
│   │   ├── Customers.jsx
│   │   ├── Addblog.jsx
│   │   ├── AddCoupon.jsx
│   │   └── ... (20+ pages)
│   ├── routing/           # Route guards
│   │   ├── OpenRoutes.jsx
│   │   └── PrivateRoutes.jsx
│   ├── utils/             # Utilities
│   │   ├── baseURL.js     # API endpoint
│   │   └── axiosConfig.js # Axios interceptors
│   ├── App.jsx            # Route definitions
│   ├── main.jsx           # Entry point
│   └── index.css          # Global styles
├── public/                # Static files
├── index.html
├── vite.config.js
└── package.json
```

---

## 5. Setup Instructions

### Prerequisites

- Node.js 18+ installed
- Backend server running on `http://localhost:5000`

### Installation

```bash
# Navigate to admin directory
cd admin

# Install dependencies
npm install

# Note: If @ant-design/plots is missing, install it:
npm install @ant-design/plots
```

### Environment Variables

Create a `.env` file in the `admin/` root:

```env
VITE_API_BASE_URL=http://localhost:5000/api
```

The hardcoded base URL is in `src/utils/baseURL.js`:

```javascript
export const baseURL = "http://localhost:5000/api";
```

### Running the Project

```bash
# Development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

Default dev server: `http://localhost:5173`

---

## 6. API Integration

The admin panel communicates with the backend via REST API:

| Endpoint                      | Purpose                     |
| ----------------------------- | --------------------------- |
| `POST /api/users/admin-login` | Admin authentication        |
| `GET /api/products`           | Fetch all products          |
| `POST /api/products`          | Create new product          |
| `PUT /api/products/:id`       | Update product              |
| `GET /api/users/all-users`    | List customers              |
| `GET /api/users/all-orders`   | List all orders             |
| `PUT /api/users/orders/:id`   | Update order status         |
| `POST /api/uploads`           | Upload images to Cloudinary |

### Axios Configuration

- Base URL configured in `src/utils/baseURL.js`
- JWT token attached via Axios interceptors
- Toast notifications for API errors

---

## 7. Scripts

| Script  | Command                 | Purpose                  |
| ------- | ----------------------- | ------------------------ |
| dev     | `vite`                  | Start development server |
| build   | `vite build`            | Create production build  |
| preview | `vite preview`          | Preview production build |
| lint    | `eslint . --ext js,jsx` | Run ESLint checks        |

---

## 8. Deployment Notes

### Build Configuration

- Vite is configured for SPA routing (see `vite.config.js`)
- Proxy settings available for API requests in development

### Production Checklist

1. Update `baseURL.js` to production API endpoint
2. Set environment variables for production
3. Run `npm run build` to generate `dist/` folder
4. Deploy `dist/` contents to static hosting (Netlify, Vercel, etc.)

### Recommended Hosting

- **Netlify**: Drag-and-drop `dist/` folder
- **Vercel**: Connect GitHub repo with auto-deploy
- **AWS S3 + CloudFront**: For enterprise deployment
