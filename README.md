# TP-8-spring

## Description
Ce projet est une application Spring Boot qui expose une API RESTful pour gérer des comptes bancaires. Elle permet d'effectuer des opérations CRUD (Create, Read, Update, Delete) sur les comptes. L'application utilise une base de données en mémoire H2 et supporte les formats JSON et XML pour les requêtes et les réponses.

<img width="1377" height="976" alt="image" src="https://github.com/user-attachments/assets/af6d3530-75fe-4aa2-8a1c-adde44f812a2" />
<img width="1407" height="969" alt="image" src="https://github.com/user-attachments/assets/a2dc1ef7-505a-456f-92b0-e8e48d5cdee2" />
<img width="1359" height="971" alt="image" src="https://github.com/user-attachments/assets/edb80f93-696c-448c-a7d5-8778d8f21187" />
<img width="1833" height="978" alt="image" src="https://github.com/user-attachments/assets/0188f08b-46fa-4078-b7c5-636c7c0fb159" />
<img width="1849" height="970" alt="image" src="https://github.com/user-attachments/assets/b374dc1f-e669-43c3-a903-cfacad923a81" />
<img width="1868" height="975" alt="image" src="https://github.com/user-attachments/assets/9848a0fc-7434-4bae-b47b-5a50815efc44" />
<img width="1915" height="973" alt="image" src="https://github.com/user-attachments/assets/19ede02a-68c5-4822-9b90-f9cd60f200b0" />


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
