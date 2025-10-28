


# 📚 Student Management System

![Java](https://img.shields.io/badge/Java-17-orange?style=for-the-badge&logo=java)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.7-brightgreen?style=for-the-badge&logo=spring)
![MySQL](https://img.shields.io/badge/MySQL-8.0-blue?style=for-the-badge&logo=mysql)
![Maven](https://img.shields.io/badge/Maven-3.9.11-red?style=for-the-badge&logo=apache-maven)

Un système de gestion des étudiants développé avec Spring Boot et MySQL, offrant une API RESTful complète pour gérer les informations des étudiants.

## 📋 Table des matières

- [Fonctionnalités](#-fonctionnalités)
- [Technologies utilisées](#-technologies-utilisées)
- [Prérequis](#-prérequis)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Utilisation](#-utilisation)
- [API Endpoints](#-api-endpoints)
- [Documentation API](#-documentation-api)
- [Tests](#-tests)
- [Démonstration](#-démonstration)
- [Structure du projet](#-structure-du-projet)
- [Auteur](#-auteur)

## ✨ Fonctionnalités

- ➕ Créer un nouvel étudiant
- 📖 Lire la liste de tous les étudiants
- 🗑️ Supprimer un étudiant
- 📊 Compter le nombre total d'étudiants
- 📅 Statistiques des étudiants par année de naissance
- 📝 Documentation API interactive avec Swagger

## 🛠️ Technologies utilisées

- **Backend Framework**: Spring Boot 3.5.7
- **Base de données**: MySQL
- **ORM**: Spring Data JPA / Hibernate
- **Build Tool**: Maven
- **Documentation API**: SpringDoc OpenAPI (Swagger)
- **Tests**: JUnit 5, Mockito
- **Version Java**: 17

## 📦 Prérequis

Avant de commencer, assurez-vous d'avoir installé :

- ☕ Java JDK 17 ou supérieur
- 🗄️ MySQL 8.0 ou supérieur
- 📦 Maven 3.9+ (ou utilisez le wrapper Maven inclus)
- 🔧 Git

## 🚀 Installation

1. **Cloner le repository**
```bash
git clone <url-du-repository>
cd student-management
```

2. **Créer la base de données MySQL**
```sql
CREATE DATABASE studentdb;
```

3. **Configurer la base de données**

Modifiez le fichier [`src/main/resources/application.properties`](src/main/resources/application.properties) avec vos informations de connexion :

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/studentdb?serverTimezone=UTC
spring.datasource.username=votre_username
spring.datasource.password=votre_password
```

4. **Compiler le projet**
```bash
./mvnw clean install
```

Ou sur Windows :
```cmd
mvnw.cmd clean install
```

## ⚙️ Configuration

Le fichier de configuration principal se trouve dans [`src/main/resources/application.properties`](src/main/resources/application.properties) :

```properties
# Nom de l'application
spring.application.name=student-management

# Configuration de la base de données
spring.datasource.url=jdbc:mysql://localhost:3306/studentdb?serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=

# Configuration JPA/Hibernate
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.hibernate.ddl-auto=update
```

## 💻 Utilisation

### Démarrer l'application

```bash
./mvnw spring-boot:run
```

Ou sur Windows :
```cmd
mvnw.cmd spring-boot:run
```

L'application sera accessible sur `http://localhost:8080`

## 🔌 API Endpoints

| Méthode | Endpoint | Description |
|---------|----------|-------------|
| `POST` | `/students/save` | Créer un nouvel étudiant |
| `GET` | `/students/all` | Récupérer tous les étudiants |
| `DELETE` | `/students/delete/{id}` | Supprimer un étudiant par ID |
| `GET` | `/students/count` | Compter le nombre total d'étudiants |
| `GET` | `/students/byYear` | Récupérer le nombre d'étudiants par année de naissance |

### Exemples de requêtes

**Créer un étudiant :**
```bash
curl -X POST http://localhost:8080/students/save \
  -H "Content-Type: application/json" \
  -d '{
    "nom": "Dupont",
    "prenom": "Jean",
    "dateNaissance": "2000-05-15"
  }'
```

**Récupérer tous les étudiants :**
```bash
curl http://localhost:8080/students/all
```

**Supprimer un étudiant :**
```bash
curl -X DELETE http://localhost:8080/students/delete/1
```

## 📖 Documentation API

La documentation interactive de l'API est disponible via Swagger UI :

```
http://localhost:8080/swagger-ui.html
```

## 🧪 Tests

Le projet inclut des tests unitaires pour les contrôleurs et services.

### Exécuter les tests

```bash
./mvnw test
```

### Classes de tests

- [`StudentManagementApplicationTests`](src/test/java/org/example/studentmanagement/StudentManagementApplicationTests.java) : Tests de contexte Spring
- [`StudentControllerTest`](src/test/java/org/example/studentmanagement/controllers/StudentControllerTest.java) : Tests unitaires du contrôleur avec Mockito

## 🎬 Démonstration

### Captures d'écran





#### Interface Swagger UI
![img_6.png](img_6.png)

#### Création d'un étudiant
![img.png](POST.png)

#### Liste des étudiants
![img_1.png](GET.png)

#### Statistiques par année
![img_3.png](get3.png)

#### count etudiant
![img_2.png](GET2.png)

#### supprimer etudiant
![img_4.png](DELETE.png)

### test unitaire
![img_5.png](img_5.png)

## 📁 Structure du projet

```
student-management/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── org/example/studentmanagement/
│   │   │       ├── StudentManagementApplication.java
│   │   │       ├── controllers/
│   │   │       │   └── StudentController.java
│   │   │       ├── entity/
│   │   │       │   └── Student.java
│   │   │       ├── repository/
│   │   │       │   └── StudentRepository.java
│   │   │       └── service/
│   │   │           └── StudentService.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
│       └── java/
│           └── org/example/studentmanagement/
│               ├── StudentManagementApplicationTests.java
│               └── controllers/
│                   └── StudentControllerTest.java
├── pom.xml
├── mvnw
├── mvnw.cmd
└── README.md
```

### Description des composants

- **[`StudentManagementApplication`](src/main/java/org/example/studentmanagement/StudentManagementApplication.java)** : Classe principale Spring Boot
- **[`StudentController`](src/main/java/org/example/studentmanagement/controllers/StudentController.java)** : Contrôleur REST gérant les endpoints
- **[`Student`](src/main/java/org/example/studentmanagement/entity/Student.java)** : Entité JPA représentant un étudiant
- **[`StudentRepository`](src/main/java/org/example/studentmanagement/repository/StudentRepository.java)** : Interface de repository pour l'accès aux données
- **[`StudentService`](src/main/java/org/example/studentmanagement/service/StudentService.java)** : Couche de service contenant la logique métier

