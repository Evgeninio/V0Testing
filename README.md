# V0Testing

## Project Overview
V0Testing is a project about using Ai "V0" for genetare Vue.js components.

## Project Structure
```
CompanyDashboard/
├─ src/                         # Source code/Components
│   └── components/             # Repository with components
        └──AnteiInspiredDashboard.vue     # Component with prompt 1
        └──ComplexDashboardLayout.vue     # Component with prompt 2
        └──PurpleDashboard.vue            # Component with prompt 3
        └──PurpleDashboardWithCards.vue   # Component with prompt 4
        └──PurpleDashboardWithTabs.vue    # Component with prompt 5
        └──PurpleFormPage.vue             # Component with prompt 6
├── main.js                  # Main JavaScript script
├── index.html               # Main html file to enter script
├── package.json             # Setting to run the project
├── .gitignore               # Git ignore file
├── README.md                # Project documentation
```
```
Promts for components:
1. Компонент с использованием стилией: https://anteihk.com/
2.Создай страницу c Sidebar слева, Header сверху страницы, далее ниже по горизонтале 9 шт. Input, справа от Input по горизонтале будет 2 шт. 
Button, далее ниже Tabs, далее ниже по вертикале 11 шт. Input, внизу страницы будет 2 шт. Button 
3. Сделай страницу с Сайдбаром, Хедером и блоком с изображениями. Под блоком добавьте две кнопки «Сохранить» и «Удалить».
4. Сделайте страницу с Сайдбаром, Хедером и горизонтальной кнопкой «Добавить» под ним. 
Ниже разместите карточки данных в три столбца с кнопками действий на каждой карточке.
5. Создайте страницу с Сайдбаром и Хедером. Под Хедером добавьте два таба, в первом табе — список с чекбоксами, во втором — форму с четырьмя полями ввода и двумя кнопками под ними. 
6. Создайте страницу с Хедером, под ним добавьте форму с четырьмя полями ввода в два ряда. Ниже формы добавьте кнопки: «Сохранить», «Отменить» и «Очистить» с такими же стилями.
```

## Review 
```
Начало работы: 
1. Понятный интерфейс, после регистрации сразу видно поля для введения промта. 
2. Все иконки сразу показывают какую цель они несут. 
3. Быстрая регистрация, проходит только по Email. 
Преимущества: 
1. Сгенерированный компонент можно рассмотреть, как в виде кода, так и уже отрендеренном виде. 
2. Доступно скачивание сгенированного компонента.
3. Возможность загружать изображений для демонстарции стилей. 
4. Использование семантических тегов в разметке. 
5. Сохраняется история чатов. 
Недостатки: 
1. Работа со стилями. Похожие стили получаются только при загруженном изоражениие. 
При запросе таких же стилей, как и "url" V0 придумывает свои.
2. Ограниченная бесплатная версия. За сутки генерирует не более 10-15 копмонентов. 
```
## Summary of usage
```
По стандарту для генерации компонентов V0 использует React. Поэтому первым запросом обязательно уточнить на каком фреймворке необходимо генерировать. Для стилизации компонентов используется Tailwind CSS(локальной подключенние будет описано в "Running the project"). 
Также V0 использует библиотеку "lucide-vue-next" для подстановки изображений. 
В заключение можно сказать, что V0 можно использовать для разработки интерфейсов, 
так как нейросеть генерирует качественные компоненты с семантической разметкой, 
а также с заготовками под функционал кнопок и других интерактивных элементов. 
```
## Branching Strategy
This project follows the Git Flow branching model:
- `main`: The production-ready branch.
- `dev`: The development branch where features are integrated.
- `feature/*`: Feature branches for developing new features.

## Getting Started

### Installation
1. Clone the repository:
    ```
    git clone git@github.com:Evgeninio/V0Testing.git
    cd V0Testing
    ```

2. Initialization packet manager
    ```
    npm init
    ```
### Installing dependecies 

1. Installing TailwindCss
```
    npm install -D tailwindcss postcss autoprefixer
    npx tailwindcss init
    Настройка файла tailwind.config.js
    Настройка файла index.css
    Создание и настройка файла postcss.config.js
    Добавление импорта в main.js
```

2. Installing lucide-vue-next
```
    npm install lucide-vue-next
```

### Running the Project
```
    npm run dev  # Start project on a local-server
```