## Технологии

### Основные инструменты

- **Vite 7.1.10** - современный сборщик с мгновенным HMR
- **Sass 1.80.6** - CSS препроцессор с расширенными возможностями
- **PostCSS 8.5.6** - трансформация CSS с плагинами

### Линтеры и форматтеры

- **ESLint 9.38.0** - статический анализ JavaScript/TypeScript кода
- **Stylelint 16.25.0** - линтер для стилей (CSS/SCSS)
- **Prettier 3.6.2** - форматтер кода

### Плагины ESLint

- `@typescript-eslint` - поддержка TypeScript
- `eslint-plugin-react` - правила для React
- `eslint-plugin-react-hooks` - правила для React Hooks
- `eslint-plugin-jsx-a11y` - проверка доступности JSX
- `eslint-plugin-prettier` - интеграция Prettier в ESLint

### Плагины Stylelint

- `stylelint-scss` - правила для SCSS
- `stylelint-order` - сортировка свойств
- `stylelint-selector-bem-pattern` - валидация BEM-методологии

### PostCSS плагины

- `postcss-preset-env` - современные CSS-фичи
- `postcss-pxtorem` - конвертация px в rem (только в production)

## Структура проекта

```
vite-starter/
├── public/                    # Статические файлы
│   └── vite.svg
├── src/
│   ├── assets/               # Ресурсы (шрифты, изображения)
│   │   └── favicons/
│   │   └── fonts/
│   │   └── icons/
│   │   └── images/
│   ├── modules/              # JavaScript модули
│   ├── styles/               # Стили приложения
│   │   ├── components/       # Стили компонентов
│   │   ├── helpers/          # SCSS утилиты
│   │   │   ├── _constants.scss    # Константы (брейкпоинты)
│   │   │   ├── _functions.scss    # SCSS функции (fluid размеры)
│   │   │   ├── _media.scss        # Медиа-запросы миксины
│   │   │   ├── _mixins.scss       # Полезные миксины
│   │   │   └── _index.scss        # Экспорт всех helpers
│   │   ├── _fonts.scss       # Подключение шрифтов
│   │   ├── _globals.scss     # Глобальные стили
│   │   ├── _normalize.scss   # Reset CSS
│   │   ├── _utils.scss       # Утилитарные классы
│   │   ├── _variables.scss   # CSS переменные
│   │   └── styles.scss       # Главный файл стилей
│   └── main.js               # Точка входа JavaScript
├── index.html                # HTML точка входа
├── vite.config.js            # Конфигурация Vite
├── eslint.config.js          # Конфигурация ESLint
├── stylelint.config.js       # Конфигурация Stylelint
├── postcss.config.js         # Конфигурация PostCSS
├── prettier.config.js        # Конфигурация Prettier
├── jsconfig.json             # Настройки JavaScript/TypeScript
├── package.json              # Зависимости и скрипты
└── .gitignore                # Игнорируемые файлы Git
```

## Конфигурация

### Vite (`vite.config.js`)

```javascript
{
  resolve: {
    alias: {
      '@': path.resolve(__dirname, './src')  // Алиас для импортов
    }
  }
}
```

### ESLint (`eslint.config.js`)

Использует **Flat Config** (новый формат):

- **Парсеры**:
  - `@babel/eslint-parser` для JS/JSX
  - `typescript-eslint` для TS/TSX
  
- **Плагины**:
  - React, React Hooks, JSX A11y для работы с React
  - Prettier для интеграции форматирования

- **Правила**:
  - Предупреждения о `console.log`
  - Строгое равенство (`===`)
  - Запятые в многострочных объектах
  - Отключен `prop-types` (для TypeScript проектов)

### Stylelint (`stylelint.config.js`)

- **Extends**: `stylelint-config-standard-scss` - стандартные правила для SCSS
- **Плагины**:
  - `stylelint-order` - автосортировка CSS свойств
  - `stylelint-selector-bem-pattern` - валидация BEM
  
- **Кастомные правила**:
  - Сортировка свойств по логическим группам
  - Отключена проверка паттернов классов (для гибкости)
  - Отключена проверка убывающей специфичности

### PostCSS (`postcss.config.js`)

- **postcss-preset-env**: 
  - Stage 2 фичи
  - Вложенность (nesting)
  - Кастомные медиа-запросы
  
- **postcss-pxtorem** (только production):
  - Конвертирует `px` в `rem`
  - Применяется ко всем свойствам
  - Работает в media queries

### Prettier (`prettier.config.js`)

```javascript
{
  semi: false,              // Без точек с запятой
  singleQuote: true,        // Одинарные кавычки
  printWidth: 80,           // Длина строки 80 символов
  trailingComma: 'es5'      // Запятые в ES5 стиле
}
```
