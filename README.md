# Platzi-Play

API REST de práctica construida con Spring Boot 3 y Java 21, integrada con LangChain4j para consumir modelos de OpenAI. Corresponde al curso de Spring Boot de Platzi.

![Java](https://img.shields.io/badge/Java%2021-007396?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring%20Boot](https://img.shields.io/badge/Spring%20Boot%203.5-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Gradle](https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white)
![LangChain4j](https://img.shields.io/badge/LangChain4j-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)

## Estado del proyecto

Proyecto en etapas iniciales del curso de Platzi. Contiene únicamente la estructura base del paquete `com.platzi.play`, un `HelloController` y un `AiService` que genera un saludo usando un modelo de OpenAI a través de LangChain4j. Aún no hay capa de persistencia ni lógica de dominio implementada.

## Stack

- Lenguaje: Java 21 (toolchain)
- Framework: Spring Boot 3.5.7 (`spring-boot-starter-web`)
- Build: Gradle con wrapper (`gradlew`)
- IA: `langchain4j-open-ai-spring-boot-starter` 1.0.0-beta1 y `langchain4j-spring-boot-starter` 1.0.0-beta1
- Testing: `spring-boot-starter-test` + JUnit Platform

## Requisitos previos

- JDK 21
- API key de OpenAI (opcional mientras se use el modelo `demo`)

## Instalación

```bash
git clone https://github.com/JeanCaicedo/Platzi-Play.git
cd Platzi-Play
./gradlew build
```

En Windows usa `gradlew.bat`.

## Configuración

Los perfiles activos se resuelven desde `application.properties`:

- `spring.application.name=platzi-play`
- `server.servlet.context-path=/platzi-play/api`
- `langchain4j.open-ai.chat-model.model-name=gpt-4o-mini`
- Perfil activo por defecto: `dev`

El perfil `dev` (`application-dev.properties`) levanta el servidor en el puerto `8090` y usa la API key `demo`. Para producción, define tu propia key sobrescribiendo `langchain4j.open-ai.chat-model.api-key` vía variable de entorno o archivo de properties externo, sin commitearla.

## Ejecución

```bash
./gradlew bootRun
```

Endpoint disponible:

- `GET /platzi-play/api/hello` — devuelve un saludo generado por el modelo de OpenAI vía LangChain4j.

## Estructura del proyecto

```
src/main/java/com/platzi/play/
├── PlatziPlayApplication.java
├── domain/
│   └── service/
│       └── PlatziPlayAiService.java   # @AiService con @UserMessage
└── web/
    └── controller/
        └── HelloController.java       # GET /hello
src/main/resources/
├── application.properties
├── application-dev.properties
└── application-prod.properties
```

## Autor

Jean Caicedo — [@JeanCaicedo](https://github.com/JeanCaicedo)
