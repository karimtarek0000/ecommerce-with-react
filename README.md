# Karma e-commerce with React

Karma is a React storefront for browsing products by category, managing a
shopping cart and wishlist, and placing and reviewing orders. It includes
registration and login flows, protected account pages, and client-side state
persistence for the cart and authentication session.

## Features

- Browse product categories and their products.
- Add products to the cart, update quantities, and remove items.
- Register and log in with validated forms and email availability checks.
- Save products to a wishlist (available to signed-in users).
- Place orders and view order history and product details.
- Persist cart and authentication state in browser storage.
- Lazy-load routes and show loading, empty, and error states.

## Tech stack

- React 18 and TypeScript
- Vite
- Redux Toolkit, React Redux, and Redux Persist
- React Router
- React Bootstrap and Bootstrap
- React Hook Form and Zod
- Axios

## Getting started

### Requirements

- Node.js 18 or newer
- npm
- A JSON-compatible API running at `http://localhost:5005`

### Install and run

```bash
npm install
npm run dev
```

Vite prints the local development URL after it starts.

The frontend sends API requests to `http://localhost:5005` (configured in
`src/services/axios-global.js`). The API is a separate service and is not
started by the frontend scripts. It must provide the routes used by the app:

- `GET /category` and `GET /products`
- `GET /users` for email availability
- `POST /register` and `POST /login`
- `GET`, `POST`, and `DELETE /wishlist`
- `GET` and `POST /orders`

The root `db.json` contains sample categories and products. Configure the API
service to use this data and provide the authentication routes before using
account, wishlist, and order features.

## Project structure

```text
.
├── db.json                         # Sample category and product data
├── index.html                      # Vite HTML entry point
├── public/                         # Static public assets
├── src/
│   ├── assets/
│   │   ├── lottieFiles/            # Loading, empty, success, and error animations
│   │   └── svg/                    # Cart, wishlist, and like icons
│   ├── components/
│   │   ├── Auth/                   # Protected-route component
│   │   ├── Form/                   # Shared form input
│   │   ├── common/                 # Header, footer, headings, and lists
│   │   ├── eCommerce/              # Products, categories, cart, and pricing
│   │   └── feedback/               # Loading, toast, animation, and skeleton UI
│   ├── hooks/                      # Feature hooks and API/state coordination
│   ├── layouts/                    # Main and profile layouts
│   ├── pages/                      # Home, catalog, cart, auth, and account pages
│   ├── routes/
│   │   └── AppRouter.tsx           # Application routes and route guards
│   ├── services/
│   │   └── axios-global.js         # Shared API base URL
│   ├── store/                      # Redux slices, async actions, and selectors
│   │   ├── auth/
│   │   ├── cart/
│   │   ├── categories/
│   │   ├── orders/
│   │   ├── products/
│   │   ├── toasts/
│   │   └── wishlist/
│   ├── styles/                     # Global styles
│   ├── types/                      # Shared TypeScript types and guards
│   ├── utils/                      # Shared utilities
│   ├── validations/                # Sign-in and sign-up schemas
│   └── main.tsx                    # React, Redux, and style entry point
├── package.json
├── tsconfig.json
└── vite.config.ts
```
