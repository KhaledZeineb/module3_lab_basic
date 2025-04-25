# Discussion Technique : API Student RESTful

## 1. Principes REST et Notre Implémentation

### Caractéristiques RESTful :
- **Client-Server** : Séparation frontend/backend via HTTP
- **Stateless** : Chaque requête contient toutes les informations nécessaires
- **Resource-Based** :
  ```java
  @RestController
  @RequestMapping("/api/students")  // Ressource nommée

Verbes HTTP :

Endpoint	        Méthode	  Action	 Code Réponse
/api/students	    POST	  Créer	     201 Created
/api/students/{id}	GET	      Récupérer	 200 OK

2. Architecture en Couches (Controller-Service-Repository)
![deepseek_mermaid_20250425_2625d3.png](../../Downloads/deepseek_mermaid_20250425_2625d3.png)
Avantages :

Testabilité : Mock facile des dépendances

Évolutivité : Modifier une couche sans affecter les autres

Réutilisation : Services partageables entre contrôleurs

3. Configuration Spring Boot vs Java EE

# application.properties (Spring Boot)
spring.datasource.url=jdbc:h2:mem:studentdb
spring.jpa.hibernate.ddl-auto=update

# VS web.xml (Java EE)
<resource-ref>
    <res-ref-name>jdbc/MyDB</res-ref-name>
    <res-type>javax.sql.DataSource</res-type>
</resource-ref>

Gains de productivité :

-80% de configuration en moins

-Serveur embarqué (pas besoin de Tomcat externe)

-Auto-configuration des dépendances

4. Migration vers une Base de Production

*Étapes pour MySQL :
Ajouter la dépendance :
<dependency>
   <groupId>mysql</groupId>
   <artifactId>mysql-connector-java</artifactId>
   <version>8.0.33</version>
</dependency>

*Configurer les propriétés :
   spring.datasource.url=jdbc:mysql://localhost:3306/studentdb?useSSL=false
   spring.datasource.username=admin
   spring.datasource.password=secret
   spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

5. Sécurité avec JWT

Workflow d'authentification :
1.Client → /api/auth/login (email/mot de passe)

2.Serveur → Génère un JWT (valide 24h)

3.Client → Envoie le JWT dans le header Authorization

*Configuration minimale :

@Bean
public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
http
.csrf().disable()
.authorizeHttpRequests(auth -> auth
.requestMatchers("/api/auth/**").permitAll()
.anyRequest().authenticated()
)
.addFilterBefore(jwtFilter(), UsernamePasswordAuthenticationFilter.class);
return http.build();
}

*Bonnes Pratiques Supplémentaires :

Validation des entrées : @Valid + DTOs

Gestion des erreurs : @ControllerAdvice

Documentation : Swagger UI (springdoc-openapi-ui)

Monitoring : Actuator + Prometheus


**Comment télécharger :**
1. Copiez tout le contenu ci-dessus
2. Collez-le dans un nouveau fichier texte
3. Enregistrez sous le nom `discussion_api_restful.md`
4. Format compatible avec :
  - GitHub/GitLab
  - Visual Studio Code
  - Tout éditeur Markdown

**Alternative :**  
[Cliquez ici pour télécharger une version prête à l'emploi](https://gist.githubusercontent.com/example/discussion_api_restful.md) (lien fictif - à remplacer par votre propre hébergement de fichier).