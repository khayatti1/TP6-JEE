# TP 6 – Résilience des microservices avec Spring Cloud Hystrix

## Description

Ce TP met en œuvre la **résilience des microservices** à l’aide de **Spring Cloud Hystrix**.
Il illustre le **Circuit Breaker Pattern** pour gérer les lenteurs et pannes d’un microservice, tout en assurant la **continuité du service** grâce à un mécanisme de **fallback** et à la supervision via **Hystrix Dashboard**.

Le projet est basé sur le microservice **Employee** avec une base **H2**.

## Architecture

Le système est composé de :

* **Microservice Employee**

  * API REST
  * Base de données H2
  * Port : 9000

* **Spring Cloud Hystrix**

  * Circuit Breaker
  * Gestion des timeouts et fallback

* **Spring Boot Actuator**

  * Exposition des métriques

* **Hystrix Dashboard**

  * Supervision en temps réel

## Fonctionnalités

* Détection des timeouts
* Circuit Breaker automatique
* Exécution d’une méthode de secours (fallback)
* Supervision du service en temps réel
* Continuité du service malgré les défaillances

## Annotations clés

* `@EnableCircuitBreaker` : activation de Hystrix
* `@EnableHystrixDashboard` : activation du dashboard
* `@HystrixCommand` : protection d’une méthode avec fallback

## Endpoints principaux

* Service Employee :

  ```
  GET /employees
  ```
* Simulation de timeout :

  ```
  GET /myMessage
  ```
* Hystrix Dashboard :

  ```
  http://localhost:9000/hystrix
  ```
* Flux Hystrix :

  ```
  http://localhost:9000/actuator/hystrix.stream
  ```

## Exécution

```bash
mvn spring-boot:run
```

## Vérifications

* Tester un appel normal au service
* Simuler un timeout sur `/myMessage`
* Vérifier l’exécution du fallback
* Observer l’état du circuit dans le dashboard Hystrix

## Screen
![1](https://github.com/user-attachments/assets/549f6e06-f631-4547-827d-5346eec3e483)
![2](https://github.com/user-attachments/assets/bede388e-1909-4950-ab19-adb181a74acd)
![4](https://github.com/user-attachments/assets/072fe4ef-657b-4964-8149-687211a668c7)
![5](https://github.com/user-attachments/assets/d6dc57f2-a269-4198-8b23-305adfaa7561)

## Principe du Circuit Breaker

* **CLOSED** : appels normaux
* **OPEN** : appels redirigés vers le fallback
* **HALF-OPEN** : test de récupération du service

## Objectifs pédagogiques

* Comprendre la résilience des microservices
* Mettre en œuvre le Circuit Breaker Pattern
* Gérer les pannes et lenteurs réseau
* Implémenter un fallback
* Superviser un service distribué

---

**MOHAMMED EL KHAYATI & MOUAD MOUDID--5IIR11-G2**
