# Game-Player-Management-Application


# Game Player Management Application – CS 230 Module Four

> A RESTful API demo secured with Basic Authentication using Dropwizard, developed for **The Gaming Room** as part of Creative Technology Solutions (CTS) consulting.

---

## 📜 Overview

This Java-based REST application demonstrates how to:
- Create and secure REST endpoints
- Authenticate and authorize users using **Basic Authentication**
- Manage access to endpoints using **role-based annotations**
- Simulate a login experience for different user types (ADMIN, USER, PLAYER, GUEST)

---

## 🧰 Tech Stack

- **Java 17**
- **Dropwizard Framework** (`io.dropwizard`)
- **Maven Project**
- **HTTP/REST + Jersey**
- **Basic Authentication (server-side only)**

---

## 🔐 User Roles & Access

| Username | Password  | Role    | Access Notes                              |
|----------|-----------|---------|-------------------------------------------|
| admin    | password  | ADMIN   | Full access (can create users)            |
| user     | password  | USER    | Can view user info by ID                  |
| player   | password  | PLAYER  | Limited access                            |
| guest    | password  | GUEST   | Limited/no access                         |

---

## 🧪 Running the App

### 1. **Import into Eclipse as a Maven Project**

Use:  
`File → Import → Existing Maven Project`

### 2. **Set Program Arguments**

Go to:
- `Run → Run Configurations → Arguments Tab → Program arguments`

Paste:
```bash
server config.yml
````

### 3. **Start the Server**

Run the `GameAuthApplication.java` file. It should start the HTTP server at:

```
http://localhost:8080
```

---

## 🔗 Sample Endpoints

### 🔐 Authentication Prompt

Open in browser:

```http
http://localhost:8080/gameusers
```

You'll see a basic username/password dialog (see example screenshot).

### 👤 View All Users

* Endpoint: `GET /gameusers`
* Access: Any authenticated role

Response:

```json
[
  {"id":1,"firstName":"Lokesh","lastName":"Gupta","email":"India"},
  {"id":2,"firstName":"John","lastName":"Gruber","email":"USA"},
  {"id":3,"firstName":"Melcum","lastName":"Marshal","email":"AUS"}
]
```

### 🔍 View User by ID

* Endpoint: `GET /gameusers/{id}`
* Access: Only `USER` role

Example:

```http
http://localhost:8080/gameusers/1
```

If unauthorized:

```json
{"code":403,"message":"User not authorized."}
```

---

## 🧱 Files and Key Components

| File                          | Purpose                                  |
| ----------------------------- | ---------------------------------------- |
| `GameAuthApplication.java`    | Main app launcher, registers controllers |
| `GameUserRESTController.java` | Defines endpoints & role restrictions    |
| `GameAuthenticator.java`      | Validates username/password              |
| `GameAuthorizer.java`         | Checks user role                         |
| `GameUser.java`               | Model class representing a user          |
| `config.yml`                  | Dropwizard configuration                 |

---

## 🧑‍💻 Developer Notes

* Uses **@RolesAllowed** annotations for access control
* Implements **Authenticator** and **Authorizer** interfaces
* Responses are returned in **JSON** format
* Use browser or Postman to test endpoints with Basic Auth headers

---

