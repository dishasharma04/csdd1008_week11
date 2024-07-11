# csdd1008_week11

# Instructor

| Instructor  | Maziar Sojoudian  |

# Simple API Server with Go and Docker

# Docker Hub Link
https://hub.docker.com/repository/docker/natishkumar02/goapiweek11/general

# git link

https://github.com/dishasharma04/csdd1008_week11



## Overview

This project is a simple API server built using the Go programming language and Docker. The server has two endpoints:
- `/`: Returns a welcome message.
- `/about`: Returns information about the API.

## Development

### Initialize Go Module

1. **Create a project directory and navigate into it:**
   ```sh
   mkdir csdd1008_week11
   cd csdd1008_week11

2. **Initialize a new Go module**
    go mod init csdd1008_week11

# create main go
package main

import (
	"fmt"
	"log"
	"net/http"
)

func homeHandler(w http.ResponseWriter, r *http.Request) {
	if r.URL.Path != "/" {
		http.NotFound(w, r)
	}
	fmt.Fprintln(w, "Welcome to the Go API Server!")
}

func aboutHandler(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintln(w, "This is the About page.")
}

func main() {
	mux := http.NewServeMux()
	mux.HandleFunc("/", homeHandler)
	mux.HandleFunc("/about", aboutHandler)

	log.Println("Starting server on :3001")
	err := http.ListenAndServe(":3001", mux)
	if err != nil {
		log.Fatalf("Error starting server: %s\n", err)
	}
}

# Commit Code
git add .
git commit -m

# Push to GitHub
git remote add origin <https://github.com/dishasharma04/csdd1008_week11.git>
git branch -M main
git push -u origin main

# Create Dockerfile

# Use the official Golang image as the base image
FROM golang:1.22

# Set the Current Working Directory inside the container
WORKDIR /app

# Copy the source from the current directory to the Working Directory inside the container
COPY . .

# Build the Go app
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main .

# Expose port 8080 to the outside world
EXPOSE 3001

# Command to run the executable
CMD ["./main"]

# Building the Docker Image
docker build -t goapiweek11:01 .

# Push Docker Image to Docker Hub
docker tag goapiweek11:01 natishkumar02/goapiweek11:01

# Push the Docker image
docker push natishkumar02/goapiweek11:01

# Team Members

| Name           | Student ID  |
|----------------|-------------|
| Disha Sharma   | 500234080   |
| Sachin Dhamija | 500223167   |
| Mandeep Kour   | 500235136   |
| Vaibhav Agrawal| 500231194   |
| Natish Kumar   | 500235460   |
| Veerpal Kaur   | 500224580   |





