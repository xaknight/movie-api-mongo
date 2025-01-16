# movie-api-mongo

A RESTful API for managing a movie watchlist, built with Go and MongoDB.

## Table of Contents

*   [About](#about)
*   [Features](#features)
*   [Getting Started](#getting-started)
    *   [Prerequisites](#prerequisites)
    *   [Installation](#installation)
    *   [Running the Application](#running-the-application)
*   [API Endpoints](#api-endpoints)

## About

This project provides a simple RESTful API for managing a list of movies, including the ability to add, view, update (mark as watched), and delete movies. It leverages Go for the backend and MongoDB as the database.

## Features

*   **Create Movie:** Add a new movie to the watchlist.
*   **Get All Movies:** Retrieve the entire movie watchlist.
*   **Mark as Watched:** Update a movie's status to 'watched' using its ID.
*   **Delete Movie:** Remove a movie from the watchlist using its ID.
*   **Delete All Movies:** Clear the entire movie watchlist.
*   **MongoDB Integration:** Uses MongoDB as the persistent data store.

## Getting Started

### Prerequisites

*   **Go:** Make sure you have Go installed on your system as per go.mod file.
*   **MongoDB:** You need a MongoDB instance running. You can use a local instance or a cloud service like MongoDB Atlas.
*   **Git:** Git is required for cloning the repository.

### Installation

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/xaknight/movie-api-mongo.git
    cd movie-api-mongo
    ```

2.  **Install dependencies:**

    ```bash
    go mod tidy
    ```

### Running the Application

1.  **Set up MongoDB connection:**
    *   Ensure your MongoDB instance is running and accessible.
    *   **Important:** Replace the placeholder connectionstring in `controller/controller.go` with your actual MongoDB connection string:
          ```go
           const connectionString = "mongodb+srv://your-username:your-password@your-cluster-url/?retryWrites=true&w=majority&appName=Cluster0"
          ```
        *Note*: Replace `your-username` with your MongoDB username, `your-password` with your password, and `your-cluster-url` with your cluster url.
    *   Ensure you have the `netflix` database and the `watchlist` collection. If they don't exist, MongoDB will create them automatically when you start the application.

2.  **Run the application:**

    ```bash
    go run main.go
    ```

    The server will start on `http://localhost:4000`.

## API Endpoints

Here's a list of the API endpoints:

*   **GET `/api/movies`**
    *   Retrieves all movies in the watchlist.
    *   Response: `JSON array` of movie objects.
*   **POST `/api/movie`**
    *   Creates a new movie entry.
    *   Request body: `JSON object` with a "movie" (string) key.
    *   Response: The created `movie` object in JSON format.
*   **PUT `/api/movie/{id}`**
    *   Marks a movie with the given `id` as watched.
    *   `{id}` is the movie's ID.
    *   Response:  The id of updated object in string format.
*   **DELETE `/api/movie/{id}`**
    *   Deletes a movie with the given `id`.
    *   `{id}` is the movie's ID.
     *   Response: The id of deleted object in string format.
*   **DELETE `/api/deleteallmovie`**
    *   Deletes all movies from the watchlist.
    *   Response: `number` of documents deleted.
