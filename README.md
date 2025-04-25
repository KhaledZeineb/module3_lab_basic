
# Student API - Documentation

![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.2.0-green.svg)
![H2 Database](https://img.shields.io/badge/H2-2.1.214-blue.svg)

## 📋 Table des matières
1. [Fonctionnalités](#-fonctionnalités)
2. [Technologies](#-technologies)
3. [Installation](#-installation)
4. [Endpoints](#-endpoints)
5. [Base de données](#-base-de-données)
6. [Sécurité](#-sécurité)
7. [Évolution](#-évolution)

## 🚀 Fonctionnalités
- CRUD complet pour les étudiants
- Architecture RESTful
- Console H2 intégrée
- Validation des données
- Gestion des erreurs centralisée

## 💻 Technologies
```text
Spring Boot 3.2.0
H2 Database (en mémoire)
Lombok
Spring Data JPA
Spring Web
```

## 🔧 Installation
1. Cloner le dépôt :
```bash
git clone https://github.com/votre-repo/student-api.git
```
2. Configurer la base de données (application.properties) :
```properties
spring.datasource.url=jdbc:h2:mem:studentdb
spring.h2.console.enabled=true
```
3. Démarrer l'application :
```bash
mvn spring-boot:run
```

## 🌐 Endpoints
| Méthode | Endpoint                | Description                  |
|---------|-------------------------|------------------------------|
| GET     | /api/students           | Liste tous les étudiants     |
| POST    | /api/students           | Crée un nouvel étudiant      |
| GET     | /api/students/{id}      | Récupère un étudiant par ID  |
| PUT     | /api/students/{id}      | Met à jour un étudiant       |
| DELETE  | /api/students/{id}      | Supprime un étudiant         |

## 🗃️ Base de données
Accès à la console H2 :  
🔗 [http://localhost:8080/h2-console](http://localhost:8080/h2-console)  
**Identifiants :**
```properties
URL:      jdbc:h2:mem:studentdb
User:     sa
Password: 
```

## 🔐 Sécurité
Pour ajouter l'authentification JWT :
1. Ajoutez la dépendance :
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```
2. Configurez les règles d'accès dans `SecurityConfig.java`

## 📈 Évolution
- [ ] Ajouter Swagger UI
- [ ] Implémenter les tests d'intégration
- [ ] Dockeriser l'application
- [ ] Ajouter le logging centralisé

### Comment convertir en PDF :
1. **Via Chrome** :
   - Ouvrez ce README dans un navigateur
   - `Ctrl+P` → Choisissez "Enregistrer au format PDF"

2. **Via VS Code** :
   - Installez l'extension "Markdown PDF"
   - Clic droit → "Export as PDF"

3. **En ligne** :
   - Copiez le contenu dans [Markdown to PDF Converter](https://md2pdf.netlify.app/)

### Fichier PDF complet disponible ici :
[📥 Télécharger student_api_docs.pdf](lien-vers-votre-pdf) *(à héberger sur votre propre espace de stockage)*
