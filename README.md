# 🎬 iMovies - Movie Ticket Booking Made Simple

A Full Stack **MERN (MongoDB, Express.js, React.js, Node.js)** Cinema Ticket Reservation and Management Platform.

---

## 📌 Project Overview
**iMovies** is a modern cinema ticket booking platform designed to streamline movie discovery, seat selection, and ticket reservations for moviegoers, while providing theatre administrators with a comprehensive management portal.

### 🌟 Key Features
* **Movie Discovery**: Real-time title search, multi-genre filtering, release dates, ratings, and certifications.
* **Movie Details**: HD poster view, YouTube trailer integration, cast list, and audience reviews with ratings.
* **Interactive Tiered Seating**: Select show date, cinema hall, and showtime with live seat selection across **Balcony (₹250)**, **Middle Class (₹180)**, and **Lower Class (₹120)**.
* **Instant Booking & E-Tickets**: Real-time seat locking, instant booking confirmation, printable e-ticket modal, and user booking history.
* **Cancellation & Seat Release**: One-click booking cancellation that automatically frees reserved seats for others.
* **Personal Watchlist**: Add and remove favorite movies with synchronized user state.
* **Admin Management Portal**: Protected dashboard with live business metrics (revenue, total bookings, active shows, movies), movie CRUD, theatre management, and showtime scheduling.
* **Offline Fallback Engine**: Seamless built-in JSON fallback store (`server/data/persistent_store.json`), allowing full functionality even if a local MongoDB service is not running.

---

## 🛠️ Technology Stack

| Layer | Technologies Used |
| :--- | :--- |
| **Frontend** | React 18, Vite, SCSS, Bootstrap 5, React Router DOM (v7), React Icons, React Toastify, Axios, Day.js |
| **Backend** | Node.js, Express.js (REST API Architecture), Node-Cron (Background jobs) |
| **Database** | MongoDB, Mongoose ODM + Persistent JSON Fallback Store |
| **Authentication** | JSON Web Tokens (JWT), Bcrypt.js (Password Hashing) |
| **Notifications** | Nodemailer (Booking confirmation transport with fallback simulation) |

---

## 🏗️ Architecture & Project Structure

```text
IMovies - Movie ticket booking made simple/
├── client/                               # Frontend Application (React 18 + Vite)
│   ├── public/
│   │   ├── posters/                      # Movie poster image assets
│   │   └── favicon.svg                   # Brand icon
│   ├── src/
│   │   ├── components/
│   │   │   ├── header/                   # Navigation bar & search
│   │   │   ├── footer/                   # Footer & copyright
│   │   │   ├── loader/                   # Loading spinner
│   │   │   └── protection/               # Protected route guards (User & Admin)
│   │   ├── hooks/
│   │   │   └── useFetch.js               # Reusable data-fetching hook
│   │   ├── pages/
│   │   │   ├── landing/                  # Hero showcase landing page
│   │   │   ├── home/                     # Movie catalog with search & genre filter
│   │   │   ├── login/                    # User & Admin login
│   │   │   ├── register/                 # User & Admin registration
│   │   │   ├── movieDetails/             # Synopsis, trailer, and reviews
│   │   │   ├── movieShows/               # Hall & showtime selection
│   │   │   ├── seatsPage/                # Interactive tiered seat map & checkout
│   │   │   ├── bookings/                 # Booking history & printable e-ticket
│   │   │   ├── favoriteShows/            # Watchlist / favorites
│   │   │   ├── profile/                  # User profile
│   │   │   ├── editUserDetails/          # Profile editing form
│   │   │   ├── admin/                    # Admin dashboard & stats
│   │   │   ├── addMovie/                 # Admin add movie
│   │   │   ├── addTheatre/               # Admin add theatre & tiers
│   │   │   ├── addShow/                  # Admin schedule showtimes
│   │   │   └── adminBookings/            # Admin reservations management
│   │   ├── App.jsx                       # Master router
│   │   ├── index.css                     # Cinema dark theme styling
│   │   └── main.jsx                      # App root
│   ├── package.json
│   └── vite.config.js                    # Vite configuration & /api proxy
│
└── server/                               # Backend Application (Node.js + Express)
    ├── data/
    │   └── persistent_store.json         # Persistent JSON fallback data store
    ├── middlewares/
    │   └── fetchUser.js                  # JWT token verification
    ├── models/
    │   ├── adminModel.js                 # Admin Schema
    │   ├── bookingModel.js               # Booking Schema
    │   ├── favoriteModel.js              # Watchlist Schema
    │   ├── movieModel.js                 # Movie Schema
    │   ├── reviewModel.js                # Reviews & Ratings Schema
    │   ├── showModel.js                  # Showtimes & Seats Schema
    │   ├── theatreModel.js               # Cinema Hall & Tier Capacities Schema
    │   └── userModel.js                  # User Schema
    ├── routes/
    │   ├── adminRoutes.js                # Admin auth & dashboard stats
    │   ├── authRoutes.js                 # User auth & profile
    │   ├── bookingRoutes.js              # Booking creation, listing & cancellation
    │   ├── favoriteRoutes.js             # Watchlist management
    │   ├── movieRoutes.js                # Movie catalog CRUD
    │   ├── reviewRoutes.js               # Reviews & ratings
    │   ├── showRoutes.js                 # Showtime scheduling & query
    │   └── theatreRoutes.js              # Theatre CRUD & tier pricing
    ├── utils/
    │   ├── db.js                         # MongoDB connection handler
    │   ├── mailer.js                     # Nodemailer confirmation transport
    │   ├── reminderService.js            # Show reminder background job
    │   ├── cleanupService.js             # Seat cleanup background job
    │   ├── seeder.js                     # Seed database script
    │   └── mockStore.js                  # Offline fallback store engine
    ├── .env                              # Environment configuration
    ├── .env.example
    ├── package.json
    └── server.js                         # Express server entry point
```

---

## 🚀 How to Run the Project Locally

### Prerequisites
* **Node.js**: v18.0.0 or higher ([Download Node.js](https://nodejs.org/))
* **npm**: v9.0.0 or higher
* **MongoDB** *(Optional)*: If MongoDB is running on `mongodb://127.0.0.1:27017/Imovies`, it connects automatically; otherwise, the built-in offline engine handles all persistence without configuration.

---

### Step 1: Start Backend Server
Open a terminal in the project root:
```bash
cd server
npm install
npm run dev
```
* Backend API runs on: **`http://localhost:3000`**

---

### Step 2: Start Frontend Client
Open a second terminal in the project root:
```bash
cd client
npm install
npm run dev
```
* Frontend application runs on: **`http://localhost:5173`**

---

## 🔑 Default Demo Accounts

For quick testing and feature walkthroughs:

### 1. Cinema Administrator Portal
* **URL**: `http://localhost:5173/admin/login`
* **Email**: `admin@imovies.com`
* **Password**: `admin1234`
* **Access**: Dashboard analytics, Add Movies, Add Theatres, Schedule Shows, Manage Bookings.

### 2. Customer User Portal
* **URL**: `http://localhost:5173/login`
* **Email**: `tanishq@example.com`
* **Password**: `user1234`
* **Access**: Browse catalog, Watchlist, Seat reservation, Checkout, Booking history & cancellation.

> *Note: New accounts can also be created via the registration forms.*

---

## 📡 RESTful API Reference

| Module | Method | Endpoint | Description | Auth Required |
| :--- | :---: | :--- | :--- | :---: |
| **Auth** | `POST` | `/api/auth/register` | Register new user account | No |
| **Auth** | `POST` | `/api/auth/login` | Authenticate user & return JWT | No |
| **Auth** | `GET` | `/api/auth/getuser` | Get current user profile | Yes (JWT) |
| **Auth** | `PUT` | `/api/auth/updateuser` | Update user profile details | Yes (JWT) |
| **Admin** | `POST` | `/api/auth/admin/register` | Register new administrator | No |
| **Admin** | `POST` | `/api/auth/admin/login` | Authenticate admin & return JWT | No |
| **Admin** | `GET` | `/api/auth/admin/stats` | Real-time platform dashboard stats | Yes (Admin) |
| **Movies** | `GET` | `/api/movie` | List movies with optional `?search=` and `?genre=` | No |
| **Movies** | `GET` | `/api/movie/getmovie/:id` | Get details of a single movie | No |
| **Movies** | `POST` | `/api/movie/addmovie` | Add new movie to catalog | Yes (Admin) |
| **Movies** | `DELETE` | `/api/movie/deletemovie/:id` | Delete movie from catalog | Yes (Admin) |
| **Theatres** | `GET` | `/api/theatre` | List all cinema halls and tier seat counts | No |
| **Theatres** | `POST` | `/api/theatre/addtheatre` | Create theatre with Balcony, Middle & Lower pricing | Yes (Admin) |
| **Theatres** | `DELETE` | `/api/theatre/deletetheatre/:id` | Delete cinema hall | Yes (Admin) |
| **Shows** | `GET` | `/api/shows` | Retrieve all scheduled shows | No |
| **Shows** | `GET` | `/api/shows/getmovieshows/:movieName` | Get active showtimes for a movie | No |
| **Shows** | `GET` | `/api/shows/getshow/:showId` | Get live seat map and booked seats for a show | No |
| **Shows** | `POST` | `/api/shows/addshow` | Schedule a showtime for a movie | Yes (Admin) |
| **Shows** | `PUT` | `/api/shows/cancelshow/:id` | Cancel show & auto-cancel attached bookings | Yes (Admin) |
| **Shows** | `DELETE` | `/api/shows/deleteshow/:id` | Delete show from system | Yes (Admin) |
| **Bookings**| `POST` | `/api/bookings/createbooking` | Confirm seat reservation & process booking | Yes |
| **Bookings**| `GET` | `/api/bookings/userbookings/:email` | Get user's booking history | Yes |
| **Bookings**| `GET` | `/api/bookings/allbookings` | List all bookings across the platform | Yes (Admin) |
| **Bookings**| `DELETE` | `/api/bookings/cancelbooking/:bookingId` | Cancel booking & immediately release seats | Yes |
| **Bookings**| `DELETE` | `/api/bookings/deletebooking/:bookingId` | Remove ticket from user's history | Yes |
| **Favorites**| `POST` | `/api/favorite/addfavorite` | Add movie to user watchlist | Yes |
| **Favorites**| `POST` | `/api/favorite/removefavorite` | Remove movie from user watchlist | Yes |
| **Favorites**| `GET` | `/api/favorite/getfavorites/:email` | Get all watchlisted movies for user | Yes |
| **Reviews** | `POST` | `/api/review/addreview` | Post a review and star rating | Yes |
| **Reviews** | `GET` | `/api/review/getreviews/:movieId` | Get audience reviews for a movie | No |

---

## 🔮 Future Enhancements & Roadmap

* **Live Payment Gateway Integration**: Integrating **Razorpay** and **Stripe** SDKs for real-world card, UPI, and net-banking transactions.
* **Real-Time Seat Synchronization**: Implementing **WebSockets (Socket.io)** for instant live seat locking across concurrent user sessions.
* **SMS & WhatsApp Ticket Dispatch**: Integrating **Twilio** / **WhatsApp Business API** for automated mobile ticket alerts with digital QR passes.
* **Food & Beverage (F&B) Pre-ordering**: Adding snack and beverage combos to the checkout flow before seat confirmation.
* **Multi-City & Theatre Filtering**: Adding city selection and GPS-based nearby cinema recommendations.
* **Loyalty & Coupon Codes**: Discount promo codes and customer reward points redeemable at checkout.

---

## 👨‍💻 Author

* **Developer**: Tanishq Agrawal
* **Project**: iMovies - Full Stack Movie Ticket Booking Platform

