# GraphQL Spring Boot Project

## Description
Ce projet est une application Spring Boot utilisant GraphQL pour gérer des comptes et des transactions. Il inclut des fonctionnalités pour ajouter, supprimer et interroger des comptes et des transactions via des requêtes et mutations GraphQL.

## Prérequis

- **Java 17**
- **Maven 3.9.9**
- Un IDE comme IntelliJ IDEA ou Visual Studio Code

## Structure du Projet
```
├── .gitattributes
├── .gitignore
├── mvnw
├── mvnw.cmd
├── pom.xml
├── src
│   ├── main
│   │   ├── java
│   │   │   └── ma
│   │   │       └── projet
│   │   │           └── graph
│   │   │               ├── controllers
│   │   │               │   ├── CompteControllerGraphQL.java
│   │   │               │   └── TransactionControllerGraphQL.java
│   │   │               ├── dto
│   │   │               │   └── TransactionRequest.java
│   │   │               ├── entities
│   │   │               │   ├── Compte.java
│   │   │               │   ├── Transaction.java
│   │   │               │   ├── TypeCompte.java
│   │   │               │   └── TypeTransaction.java
│   │   │               ├── exception
│   │   │               │   └── GraphQLExceptionHandler.java
│   │   │               ├── repositories
│   │   │               │   ├── CompteRepository.java
│   │   │               │   └── TransactionRepository.java
│   │   │               └── GraphApplication.java
│   │   └── resources
│   │       ├── application.properties
│   │       └── graphql
│   │           └── schema.graphqls
│   └── test
│       └── java
│           └── ma
│               └── projet
│                   └── graph
│                       └── GraphApplicationTests.java
```

## Installation

1. **Clonez le dépôt GitHub** :

   ```bash
   git clone https://github.com/votre-utilisateur/votre-repo.git
   cd votre-repo
   ```

2. **Assurez-vous d'avoir Java 17 et Maven installés** sur votre machine.

3. **Installez les dépendances Maven** :

   ```bash
   mvn install
   ```

4. **Démarrez l'application** :

   ```bash
   mvn spring-boot:run
   ```

## Configuration

Le fichier de configuration principal est `src/main/resources/application.properties` :

```properties
spring.datasource.url=jdbc:h2:mem:banque
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
server.port=8082
spring.jpa.hibernate.ddl-auto=update
spring.graphql.graphiql.enabled=true
```

## Utilisation de GraphQL

Vous pouvez accéder à l'interface **GraphiQL** pour tester les requêtes et mutations GraphQL à l'adresse [http://localhost:8082/graphiql](http://localhost:8082/graphiql).

## Exemples de Requêtes

### Récupérer tous les comptes

```graphql
query {
  allComptes {
    id
    solde
    dateCreation
    type
  }
}
```

### Ajouter une transaction

```graphql
mutation {
  addTransaction(transactionRequest: {
    compteId: 1,
    montant: 1000.0,
    date: "2023-10-01",
    type: DEPOT
  }) {
    id
    montant
    dateTransaction
    type
    compte {
      id
      solde
    }
  }
}
```

# Vidéo Démonstrative

https://github.com/user-attachments/assets/0a3dbd5b-df40-4e21-aa6c-5826ba42714d

