# Используем легкий образ с OpenJDK 17
FROM eclipse-temurin:17-jdk

# Рабочая директория
WORKDIR /app

# Копируем pom.xml (для зависимостей)
COPY pom.xml .

# Кэшируем зависимости (через volume ~/.m2)
# Если зависимости уже на хосте, этого можно не делать
# RUN mvn dependency:go-offline

# Копируем весь проект
COPY . .

# Открываем порт приложения
EXPOSE 8080

# Запуск Spring Boot в dev режиме
CMD ["mvn", "spring-boot:run", "-Dspring-boot.run.jvmArguments=-Xms128m -Xmx512m"]
