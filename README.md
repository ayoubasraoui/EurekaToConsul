# TP 2 : Migration de Eureka à Consul

Ce projet détaille les étapes de la migration d'un ensemble de microservices utilisant Eureka vers Consul. L'objectif est de moderniser l'architecture de découverte de services en adoptant Consul, un outil open-source de HashiCorp offrant des fonctionnalités robustes de découverte de services, de gestion de configuration et de segmentation réseau.

## Etapes de la Migration

### 1. Lancement des Projets Localement
- Importez les projets depuis le dépôt Git suivant : [ms-arch-TP1](https://github.com/yabouqora/ms-arch-TP1.git).
- Lancez les projets localement pour confirmer leur bon fonctionnement initial.

### 2. Installation de Consul
- Téléchargez Consul à partir du site officiel : [Consul Installation](https://developer.hashicorp.com/consul/install).
- Décompressez le fichier téléchargé dans un dossier sur votre disque (par exemple, `C:\consul`).
- Ajoutez le chemin du dossier à la variable d'environnement `PATH`.
- Démarrez Consul en mode développement avec la commande :
  ```bash
  consul.exe agent -dev

 - Accédez à l'interface web de Consul via http://localhost:8500.
### 3. Configuration des Projets pour Consul
 - Remplacez la dépendance Eureka par celle de Consul dans les fichiers pom.xml :
  ```bash
   <dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-consul-discovery</artifactId>
    </dependency>

 - Modifiez la configuration pour chaque projet, par exemple :
  spring:
  cloud:
    consul:
      host: localhost
      port: 8500
      discovery:
        service-name: SERVICE-CLIENT
  application:
    name: SERVICE-CLIENT
- Ajoutez l'annotation @EnableDiscoveryClient dans la classe principale de chaque service :
   @SpringBootApplication
@EnableDiscoveryClient
public class ClientServiceApplication {
    public static void main(String[] args) {
        SpringApplication.run(ClientServiceApplication.class, args);
    }
}
### 4.Test des Services
- Testez les services pour vérifier le bon fonctionnement de la migration vers Consul.
# Conclusion :
- En suivant ces étapes, vous devriez avoir migré avec succès votre projet de Eureka à Consul, bénéficiant ainsi d'une infrastructure de découverte de services plus flexible et moderne.
