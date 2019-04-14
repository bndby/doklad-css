# План доклада

## 1. Приветствие и краткая информация о себе / 1-2 мин

## 2. Варианты создания стилей / 3-4 мин

Краткий смысл, сравнение достоинств и недостатков:

* Чистый CSS
* Препроцессоры: SASS/SCSS, LESS, Stylus
* Постпроцессоры: PostCSS

## 3. Инструментарий / 5 мин

* gulp 4
* gulp-postcss
* postcss-preset-env / cssnext - набор плагинов которые реализуют будущие стандарты
* postcss-import - как пример плагина без стандартов
* postcss-rtl - как пример плагина-генератора доп. кода

Также полезно, но без подробностей в докладе:

* stylelint - лайв-ревью стилей
* gulp-sourcemaps - для создания карт кода
* gulp-csso - минификация CSS

## 4. Практика - 10 мин

1. Разбор куска gulp-конфига, с объяснением некоторых параметров и плагинов

```javascript
const postcssOptions = [
	atImport(),
	postcssPresetEnv({
		stage: 0,
		autoprefixer: {
			grid: true,
			browsers: [ 'last 4 versions', 'ie >= 11', 'iOS >= 9' ]
		}
	})
]

const devCss = () => {
	return gulp.src( './src/assets/css/*.css' )
		.pipe( sourcemaps.init() )
		.pipe( postcss( postcssOptions ) )
		.pipe( sourcemaps.write( '.' ) )
		.pipe( gulp.dest( './dev/assets/css' ) )
task( 'DEV', gulp.series( devCss ) )

```

2. Методики организации CSS и БЕМ (?)

3. Grid-раскладка в IE10+ - как настроить и использовать

4. Flex и dir=rtl

5. Склейка локальных импортов

6. Custom properties аля переменные

7. Вложенные селекторы и &

8. Media queries

