# ScheduleMicroService

Сервис расписания GatherForge.

Здесь создаются игровые сессии: мастер указывает место и время игры,
добавляет участников и управляет статусом сессии.

## Что делает сервис

- создаёт и хранит игровые сессии;
- позволяет менять время, место и статус игры;
- добавляет и удаляет участников;
- сохраняет выбранного игроком персонажа;
- проверяет пользователей и персонажей через UserControllerMicroService;
- отправляет событие о запланированной игре через Kafka.

## Стек

.NET 8, ASP.NET Core, PostgreSQL, gRPC, Kafka, Swagger.

## Связанные сервисы

- [Gateway](https://github.com/GatherForge/Gateway) — принимает внешние
  запросы и передаёт их сервису;
- [UserControllerMicroService](https://github.com/GatherForge/UserControllerMicroService)
  — хранит пользователей и персонажей;
- [GameEventsMicroservice](https://github.com/GatherForge/GameEventsMicroservice)
  — получает информацию о запланированной игре.

## Локальный запуск

Для работы нужны PostgreSQL, Kafka и запущенный
UserControllerMicroService.

```bash
dotnet restore Schedule.sln
dotnet run --project src/Schedule/Schedule.csproj
```

Настройки подключений находятся в файле:

`src/Schedule/appsettings.Local.json`
