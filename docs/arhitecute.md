# Архитектура

Для начала, давайте опишем каждую папку в вашей структуре проекта и назначение, которое она выполняет в приложении Nuxt 3 (Vue 3). Это будет основой для документации по архитектуре вашего приложения.

### Api
Папка для хранения API-запросов к серверу. Обычно здесь содержатся функции или классы, которые инкапсулируют логику HTTP-запросов с использованием библиотек типа axios или fetch.

### App
Папка Nuxt 3 для объявления различных конфигураций приложения

### Assets
Содержит статические файлы, такие как изображения, стили CSS, шрифты и другие медиафайлы, которые используются в приложении.

### Components
Компоненты Vue, которые могут быть повторно использованы по всему приложению. Внутри этой папки есть подпапки:
1. `core` - общие компоненты, доступные во всем приложении.
2. `layout` - компоненты, отвечающие за структуру страниц, такие как header, footer, aside и т.д.
3. `ui` - компоненты пользовательского интерфейса, такие как кнопки, формы и т.д.

### Composables
Функции, используемые Composition API Vue 3. Эти функции обычно предоставляют логику состояния и методы, которые могут быть переиспользованы в различных компонентах.

### Configs
Настройки различных модулей приложения, которые затем импортируются в `nuxt.config.ts`. Это может включать в себя конфигурации для плагинов, миксинов, маршрутов и т.д.

### Environments
Файлы конфигурации для окружений, таких как Kubernetes (k8s) или Docker.

### Layouts
Глобальные макеты страниц, которые определяют общий вид страниц приложения.

### Locales
Файлы локализации для поддержки интернационализации (i18n), позволяющей переключаться между языками.

### Middleware
Middleware Nuxt 3, которые позволяют выполнять действия перед рендерингом страницы или группой страниц.

### Modules
Модули Nuxt 3, которые расширяют функциональность приложения, например, добавляют новые маршруты

### Pages
Маршрутизируемые компоненты Vue, которые соответствуют URL-маршрутам вашего приложения.

### Plugins
Плагины Nuxt 3, которые добавляют глобальную функциональность в приложение

### Public
Публичная папка, которая служит для размещения статических файлов, доступных прямо из корня.

### Server
Серверная часть приложения, включая серверные middleware, API-роуты и другие серверные функции.

### Shared
Общие ресурсы, используемые по всему приложению:
1. constants - константы, используемые в приложении.
2. models - модели данных, которые представляют сущности приложения.
3. services - сервисы, инкапсулирующие бизнес-логику приложения.
4. types - типы TypeScript, используемые в приложении.

### Stores
Хранилища для Pinia

### Utils
Утилитарные функции и хелперы, которые могут быть использованы в разных частях приложения.
ВАЖНО! - В отличии от `Composables` - функции, которые можно использовать в директории `/utils/`, должны быть универсальными и не связанными напрямую с `vue`, `nuxt` и служить для облегчения общего кода.

## Предназначение и область использования
1. Если вы создаете компонент, который будет использоваться в нескольких местах и не имеет специфической бизнес-логики, он должен быть помещен в `/components/ui/`
2. Если вы создаете API-запросы, они должны быть помещены в `/api/`, чтобы отделить логику запросов от компонентов и улучшить переиспользуемость. Так же нужно обновить `/shared/models/`, добавив модель для работы с данными api. При необходимости добавить типы и константы 
3. Утилиты (`/utils/`) должны содержать общие функции, которые могут быть использованы в разных частях приложения, например, функции для работы с датами или строками.
4. Композиции (`/composables/`) должны использоваться для инкапсуляции логики состояния и поведения, которые могут быть переиспользованы в компонентах.
5. Модели (`/shared/models/`) и сервисы (`/shared/services/`) должны быть использованы для организации бизнес-логики и работы с данными.
6. Константы (`/shared/constants/`) и типы (`/shared/types/`) должны использоваться для определения глобальных значений и типов, которые используются во всем приложении
