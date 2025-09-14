# asp-net-template project - clean architecture

Микросервис построен по принципам Clean Architecture с четким разделением слоев и зависимостей

## Структура проектов

| Проект | Назначение | Зависимости |
|--------|------------|-------------|
| **asp-net-template.API** | Web API, контроллеры, точка входа | Application, Infrastructure |
| **asp-net-template.Application** | Бизнес-логика, сервисы, use cases | Domain |
| **asp-net-template.Domain** | Доменные модели, интерфейсы, entities | - |
| **asp-net-template.Infrastructure** | Данные, внешние сервисы, repositories | Application |


## Быстрая настройка

### Добавить все проекты в solution

```bash
dotnet sln add src/Services/asp-net-template/**/*.csproj
```

### Или добавить проекты по отдельности

```bash
# API-слой (зависит от Application, Infrastructure)
dotnet sln add "src/Services/asp-net-template/asp-net-template.API/asp-net-template.API.csproj"

# Слой приложения (зависит от Domain)
dotnet sln add "src/Services/asp-net-template/asp-net-template.Application/asp-net-template.Application.csproj"

# Доменный слой (без зависимостей)
dotnet sln add "src/Services/asp-net-template/asp-net-template.Domain/asp-net-template.Domain.csproj"

# Инфраструктурный слой (зависит от Application)
dotnet sln add "src/Services/asp-net-template/asp-net-template.Infrastructure/asp-net-template.Infrastructure.csproj"
```

## Сборка и запуск

```bash
# Восстановить зависимости
dotnet restore

# Собрать проект
dotnet build

# Запустить API
dotnet run --project src/Services/asp-net-template/asp-net-template.API
```

## Проверка настройки

```bash
# Просмотреть все проекты в solution
dotnet sln list

# Проверить зависимости проектов
dotnet list src/Services/Capasp-net-template/asp-net-template.API reference
```

## Архитектурные принципы

### Инверсия зависимостей
> Domain не зависит ни от чего.

### Разделение ответственности
> Каждый слой имеет чёткое назначение, бизнес-логика изолирована от внешних зависимостей.

### Расширяемость
> Легко добавлять новую функциональность.