# TP-8-spring

## Description
Ce projet est une application Spring Boot qui expose une API RESTful pour gérer des comptes bancaires. Elle permet d'effectuer des opérations CRUD (Create, Read, Update, Delete) sur les comptes. L'application utilise une base de données en mémoire H2 et supporte les formats JSON et XML pour les requêtes et les réponses.

## Project Structure
```
.
├───.mvn
│   └───wrapper
│       └───maven-wrapper.properties
├───src
│   ├───main
│   │   ├───java
│   │   │   └───org
│   │   │       └───example
│   │   │           └───tp8spring
│   │   │               ├───Tp8SpringApplication.java
│   │   │               ├───controllers
│   │   │               │   └───CompteController.java
│   │   │               ├───entities
│   │   │               │   ├───Compte.java
│   │   │               │   └───TypeCompte.java
│   │   │               └───repositories
│   │   │                   └───CompteRepository.java
│   │   └───resources
│   │       ├───application.properties
│   │       ├───static
│   │       └───templates
│   └───test
│       └───java
│           └───org
│               └───example
│                   └───tp8spring
│                       └───Tp8springApplicationTests.java
├───.gitattributes
├───.gitignore
├───mvnw
├───mvnw.cmd
└───pom.xml
```

## Technologies Used
- Java 17
- Spring Boot 3
- Spring Data JPA
- Spring Web
- H2 Database
- Lombok
- SpringDoc OpenAPI (Swagger UI)
- Jackson (for JSON and XML support)
- Maven

## Functionalities
L'API expose les endpoints suivants pour la gestion des comptes :

- **`GET /banque/comptes`**: Récupérer la liste de tous les comptes.
- **`GET /banque/comptes/{id}`**: Récupérer un compte par son identifiant.
- **`POST /banque/comptes`**: Créer un nouveau compte.
- **`PUT /banque/comptes/{id}`**: Mettre à jour un compte existant.
- **`DELETE /banque/comptes/{id}`**: Supprimer un compte.

### Modèle de Données `Compte`
| Attribut      | Type         | Description                               |
|---------------|--------------|-------------------------------------------|
| `id`          | `Long`       | Identifiant unique du compte (auto-généré) |
| `solde`       | `double`     | Solde du compte                           |
| `dateCreation`| `Date`       | Date de création du compte                |
| `type`        | `TypeCompte` | Type de compte (`COURANT` ou `EPARGNE`)   |

## How to run the application
Pour lancer l'application, vous pouvez utiliser la commande Maven suivante à la racine du projet :
```bash
./mvnw spring-boot:run
```
L'application sera alors accessible à l'adresse `http://localhost:8080`.

## How to use the API

### Documentation Swagger
Une fois l'application lancée, la documentation Swagger UI est disponible à l'adresse suivante pour tester les endpoints :
[http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)

### Exemples de requêtes cURL

#### Créer un compte (JSON)
```bash
curl -X POST http://localhost:8080/banque/comptes \
-H "Content-Type: application/json" \
-d '{
    "solde": 1000.0,
    "dateCreation": "2025-11-08",
    "type": "COURANT"
}'
```

#### Créer un compte (XML)
```bash
curl -X POST http://localhost:8080/banque/comptes \
-H "Content-Type: application/xml" \
-d <Compte>
    <solde>1500.0</solde>
    <dateCreation>2025-11-08</dateCreation>
    <type>EPARGNE</type>
</Compte>
```

#### Récupérer tous les comptes (JSON)
```bash
curl -X GET http://localhost:8080/banque/comptes -H "Accept: application/json"
```

#### Récupérer tous les comptes (XML)
```bash
curl -X GET http://localhost:8080/banque/comptes -H "Accept: application/xml"
```

#### Mettre à jour un compte
```bash
curl -X PUT http://localhost:8080/banque/comptes/1 \
-H "Content-Type: application/json" \
-d '{
    "solde": 1200.0,
    "dateCreation": "2025-11-08",
    "type": "COURANT"
}'
```

#### Supprimer un compte
```bash
curl -X DELETE http://localhost:8080/banque/comptes/1
```
