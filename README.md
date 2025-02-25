# Inventory Management System

## Overview
The **Inventory Management System** is designed to streamline inventory management for local provision stores. This platform allows users to explore a wide range of products, add items to their cart, and make secure payments via the **Razorpay payment gateway**. Once an order is placed, users can track their purchases in the **Orders** section.

The system also includes an **admin panel** that provides store owners with full control over inventory. Admin users can:
- **Manage Products**: Add, update, or delete items, including modifying quantities, images, names, and categories.
- **Track Orders**: View and manage all user orders efficiently.

🔗 **Live Website**: [Inventory Management System](https://ravi-traders.netlify.app/)

## Tech Stack
### **Frontend:**
- **Framework:** React.js
- **State Management:** React Context API
- **Styling:** CSS Modules / Global CSS
- **Routing:** React Router
- **Package Manager:** npm

### **Backend:**
- **Environment:** Node.js with Express.js
- **Database:** MongoDB (via Mongoose ORM)
- **Authentication:** JSON Web Tokens (JWT)

### **Other Technologies Used:**
- **API Requests:** Fetch API
- **Security:** bcrypt.js (for password hashing)
- **Validation:** Express-validator
- **Payment Gateway:** Razorpay

## **Hooks Used in the Project**
### 1. `useState`
The `useState` hook is widely used across various components to manage local state. In `AddItem.js`, it helps store and update form input values when adding new items. Similarly, in `Item.js`, it manages the frequency state of an item to track how often it is used. `Items.js` uses it to track updates to item data, while `Login.js` and `Signup.js` rely on `useState` for handling user credentials during authentication. Additionally, in `AlertProvider.js`, `CartProvider.js`, `ItemsProvider.js`, and `UserProvider.js`, `useState` manages global states such as alerts, cart items, user progress, and order information.

#### Example from `AddItem.js`:
```js
const [item, setItem] = useState({
  name: "", qty: "", price: "", unit: "", category: "", imageURL: ""
});
```

---

### 2. `useEffect`
The `useEffect` hook is primarily used for handling side effects, such as fetching data when a component is mounted. In `Items.js`, it automatically retrieves the list of available items when the component loads. Similarly, in `Orders.js`, it fetches user orders upon mounting to ensure that the most up-to-date order data is displayed.

#### Example from `Items.js`:
```js
useEffect(() => {
  getAllItems();
}, []);
```

---

### 3. `useContext`
The `useContext` hook enables access to shared state across multiple components. In `App.js`, it is used to retrieve and manage the global progress state. `AddItem.js` makes use of `useContext` to interact with the `ItemsContext` and `ProgressContext`, ensuring item-related data is consistently managed. Components such as `Cart.js`, `Item.js`, and `Items.js` rely on `CartContext` and `ItemsContext` to manage cart interactions and display items properly. Meanwhile, `Login.js` and `Signup.js` use `AlertContext`, `ProgressContext`, and `UserContext` to provide user feedback and handle authentication processes. The navbar also utilizes `CartContext` to display the current cart status.

#### Example from `Cart.js`:
```js
const { cartItems, totalCost, placeOrder } = useContext(CartContext);
```

---

### 4. `useRef`
The `useRef` hook is used for direct DOM interactions without triggering re-renders. In `AddItem.js`, it is used to close modals dynamically without affecting component state. `Items.js` also leverages `useRef` for handling modal actions more efficiently.

#### Example from `AddItem.js`:
```js
const closeRef = useRef(null); // Holds reference to close button for popup modal
```

---

## **Installation**
```sh
# Clone the repository
git clone https://github.com/YKGupta/PEP-Project.git
cd PEP-Project

# Install frontend dependencies
cd frontend
npm install

# Install backend dependencies
cd ../Backend
npm install
```

## **Running the Project**
```sh
# Start frontend
cd frontend
npm start

# Start backend
cd ../Backend
node index.js
```

## **Environment Variables**
Create a `.env` file in the Backend folder and add:
```
KEY_ID=<YOUR RAZORPAY KEY ID>
KEY_SECRET=<YOUR RAZORPAY KEY SECRET>
MONGO_URI=<YOUR DATABASE CONNECTION URI>
SECRET_KEY=<YOUR SECRET KEY FOR JWT>
```

Create a `.env` file in the frontend folder and add:
```
REACT_APP_HOST=<BACKEND URL>
```

---

## **Contributing**
There are currently no restrictions on contributions. Feel free to submit a merge request, and your changes will be reviewed.

## **License**
This project is licensed under the **MIT License**, making it open-source and free for modification and distribution.
