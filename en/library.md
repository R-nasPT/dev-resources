# Development Libraries

### Routing
- `react-router-dom`: Routing for React applications.
- `@tanstack/router`: A powerful routing library for React applications with features like nested routes and data loading.
- `@tanstack/router-devtools`: Development tools for inspecting and debugging routing in applications that use `@tanstack/router`.

### Forms & Validation
- `@tanstack/react-query`: Data fetching and caching.
- `@tanstack/react-query-devtools`: Tools for debugging and inspecting queries in `@tanstack/react-query`.
- `swr` (stale-while-revalidate): React Hooks for data fetching.
- `react-hook-form` & `@hookform/resolvers`: Form handling in React.
- `yup` | `zod` | `joi` | `ajv`: Schema validation libraries.

### Data Fetching & State Management
- `axios` | `use-axios-client`: HTTP client libraries for making API requests.
- `@reduxjs/toolkit` | `react-redux`: State management using Redux in React.
- `zustand`: Lightweight state management library.

### Utility Libraries
- `lodash` & `@types/lodash`: Utility functions for JavaScript.

### Select & Dropdown
- `react-select`: Customizable select input component.
- `react-animate-height`: Animate height for dropdown sliding effects.
- `react-tailwindcss-datepicker`: Datepicker component styled with Tailwind CSS.

### Charts
- `chart.js` & `react-chartjs-2`: For data visualization in React.
- `Recharts`: A composable charting library built on React components.

### Drag and Drop
- `react-beautiful-dnd`: Drag-and-drop interface building library.
- `react-dnd` & `react-dnd-html5-backend`: Flexible drag-and-drop utilities.

### Animation
- `gsap` (GreenSock): Advanced animation library.
- `Framer Motion`: Animation library for React.
- `React Spring`: Spring physics-based animation.
- `react-reveal` | `react-awesome-reveal` | `ScrollReveal`: Scroll-based animation libraries.

### Text Animation
- `react-type-animation`: Typewriter effect animation.
- `react-random-reveal`: Random text revealing effect.
- `react-countup`: Animated count up component.
- `react-text-loop` | `react-text-loop-next`: Looping text animation.
- `react-fast-marquee`: Marquee-style text scrolling.
- `react-fade-in`: Fade-in animation for React.

### Multiple Hooks
- `react-use`: Collection of essential React hooks.
- `@uidotdev/usehooks`: A variety of custom hooks.
- `usehooks-ts`: Typed hooks for TypeScript in React.

### Tailwind Support
- `tailwind-merge`: Merge Tailwind CSS classnames.
- `clsx`: Utility for conditionally joining classnames.
- `classix`: Fast classnames utility.
- `classnames`: Utility for classnames management.
- `tailwind-variants`: Variants pattern for Tailwind CSS.
- `class-variance-authority`: Utility for Tailwind CSS variants.
- `windstitch`: Tailwind CSS styling helper.

#### Combined Utility
- **Using `twMerge` and `clsx`:** 
  ```javascript
  const cn = twMerge(clsx(...));
  ```
  This combination is used to merge Tailwind CSS classes with conditional logic for improved class management.

### Document & Media Processing
- `react-to-print`: Library for printing React components.
- `@react-pdf/renderer`: Library for creating PDF documents in React.
- `react-pdf-tailwind`: Styling for PDFs using Tailwind CSS.
- `react-barcode`: Barcode generator for React.
- `react-qr-code`: QR code generator for React.
- `@zxing/library`: Library for barcode scanning.
- `react-media-recorder`: Library for recording audio and video in React.
- `exceljs`: Library for reading, manipulating, and writing spreadsheet data.

### Date and Time Libraries
- `date-fns`: A modern JavaScript date utility library for parsing, formatting, and manipulating dates.
- `@date-fns/tz`: Time zone support for date-fns.
- `@date-fns/utc`: UTC support for date-fns.
- `dayjs`: A lightweight alternative to Moment.js for manipulating dates.

---

## BACK END

### Both (JS & TS)
- `dotenv`: Load environment variables.
- `express`: Web framework for Node.js.
- `cors`: Enable cross-origin resource sharing.

### JavaScript
- `nodemon`: Automatically restart Node.js applications.

### TypeScript
- `@types/express`: Type definitions for Express.js.
- `typescript` & `ts-node`: TypeScript support for Node.js.
- `ts-node-dev`: TypeScript development environment for Node.js.
- `@types/cors`: Type definitions for `cors`.

---

## Authentication

### Front-end
- `jwt-decode`: Decode JWT tokens.

### Back-end
- `(bcrypt & @types/bcrypt)` | `(bcryptjs & @types/bcryptjs)` | `bcrypt-ts`: Hashing passwords.
- `@types/jsonwebtoken` & `jsonwebtoken`: JWT handling for authentication.
- **Tip (Simplified)**: `jose`: A utility library for handling JWT and JWS.

---

## Encrypt/Decrypt

- `crypto-js` & `@types/crypto-js`: Cryptography library for encrypting and decrypting data.
- `libsodium-wrappers` & `@types/libsodium-wrappers`: Secure encryption and decryption.
- **Tip (Simplified)**: `cryptr`, `node-encryption`: Simplified encryption utilities.

---

## Socket.io

### Front-end
- `socket.io-client`: WebSocket client for real-time communication.

### Back-end
- `socket.io`: WebSocket server for real-time applications.

---

# Utility Commands

## Create Secret Key
To generate a secret key, run the following command in your terminal:

```bash
node -e "console.log(require('crypto').randomBytes(256).toString('base64'));"
```

This command will output a random 256-byte string encoded in base64, suitable for use as a secret key in your applications.
