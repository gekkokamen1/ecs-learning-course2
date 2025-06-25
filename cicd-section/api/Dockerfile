
#1 build
FROM gradle:jdk21 AS build
WORKDIR /app
COPY . /app
RUN chmod +x ./gradlew && \
    ./gradlew build

# アプリ実行
FROM openjdk:21
# --from=build->#1から/app/build/libs/my-app-0.0.2-SMAPSHOT.jarをコピー
#　コピー先./my-app.jar
COPY --from=build /app/build/libs/my-app-0.0.1-SNAPSHOT.jar ./my-app.jar
# コンテナとして起動
CMD [ "java","-jar","my-app.jar" ]
