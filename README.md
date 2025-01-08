Sure! Here’s the complete `README.md` file in a single block of code for your GitHub repository:

```markdown
# Emotorad Backend Task

This is a backend application for Emotorad that uses SQLite and Sequelize ORM to manage contacts. The server is built using Express.js and handles endpoints to identify and manage contacts based on email and phone number.

## Prerequisites

Before you begin, ensure that you have met the following requirements:

- **Node.js** and **npm** installed on your machine.
- **SQLite** installed on your machine.

### Install Node.js and npm (if not already installed)

1. Update your package list:
   ```bash
   sudo apt update
   ```

2. Install Node.js and npm:
   ```bash
   sudo apt install nodejs npm
   ```

3. Verify the installation:
   ```bash
   node -v
   npm -v
   ```

   If you have Node.js and npm installed already, you can skip this step.

### Install SQLite

1. Download and install SQLite:
   ```bash
   sudo apt install sqlite3
   ```

2. Verify SQLite installation:
   ```bash
   sqlite3 --version
   ```

## Project Setup

1. **Clone the repository:**

   If you haven't already cloned the repository, you can clone it using the following command:

   ```bash
   git clone https://github.com/your-username/emotorad-backend-task.git
   ```

   Replace `your-username` with your actual GitHub username.

2. **Navigate to the project directory:**

   ```bash
   cd emotorad-backend-task
   ```

3. **Install project dependencies:**

   Inside the project directory, install all dependencies listed in `package.json`:

   ```bash
   npm install
   ```

## Running the Application

1. **Start the server:**

   To start the application, run the following command:

   ```bash
   npm start
   ```

   This will start the server on `http://<IP_Address>:3000`.

2. **Verify the server is running:**

   Open your browser or use `curl` to verify that the application is working:

   ```bash
   curl http://<IP_Address>:3000
   ```

   You should receive the following response:

   ```
   Welcome to the Emotorad Backend Task API
   ```

## Curl
This is the command we use to send the request to the API to store the data in the database.

### User1 
``` bash
curl -X POST http://98.84.159.39:3000/identify -H "Content-Type: application/json" -d '{"email": "user1@example.com", "phoneNumber": "1234567890"}'
```
### User2
``` bash
curl -X POST http://98.84.159.39:3000/identify -H "Content-Type: application/json" -d '{"email": "user2@example.com", "phoneNumber": "1231231230"}'
```
### User3
``` bash
curl -X POST http://98.84.159.39:3000/identify -H "Content-Type: application/json" -d '{"email": "user3@example.com", "phoneNumber": "1234569870"}'
```

## Test Cases
### Test Case 1: Test the API to store the data in the database if the Mobile Number is already present in the database.
``` bash
curl -X POST http://98.84.159.39:3000/identify -H "Content-Type: application/json" -d '{"email": "user2_new@example.com", "phoneNumber": "1231231230"}'
```
### Test Case 2: Test the API to store the data in the database if the Email Id is already present in the database.
``` bash
curl -X POST http://98.84.159.39:3000/identify -H "Content-Type: application/json" -d '{"email": "user3@example.com", "phoneNumber": "4564564568"}'
```

## Database

The project uses SQLite for data storage. The SQLite database is created automatically when you run the application for the first time. The database file is stored in the project directory as `database.sqlite`.

### Database Schema

The `Contact` table has the following columns:

- `id`: Primary key, auto-incremented integer.
- `phoneNumber`: The contact's phone number (optional).
- `email`: The contact's email address (optional).
- `linkedId`: Foreign key linking secondary contacts to primary contacts (optional).
- `linkPrecedence`: Enum value (`primary` or `secondary`) indicating whether the contact is primary or secondary.
- `createdAt`: Timestamp when the contact was created.
- `updatedAt`: Timestamp when the contact was last updated.
- `deletedAt`: Timestamp when the contact was deleted (optional).
