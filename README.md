# md2html

Программа преобразует набор md-файлов в html. Предназначена для написания документации движка [Dviglo](https://github.com/Dviglo/Dviglo),
но можно использовать и для хранения записей на своём компьютере (но лучше для этого использовать [IMV](https://github.com/1vanK/MarkdownViewer)).
В отличие от обычного Markdown поддерживает формулы в формате LaTeX и теги.

## Скачивание и компиляция (Windows)

```
:: Меняем кодировку консоли на UTF-8
chcp 65001

:: Указываем путь к Git и CMake
set "PATH=c:\Program Files\Git\bin;c:\Programs\CMake\bin"

:: Качаем репозиторий в папку Repo
git clone https://github.com/Dviglo/md2html Repo

:: Создаём проекты в папке Build
cmake Repo -B Build

:: Компилируем
cmake --build Build

:: Ждём нажатия ENTER перед закрытием консоли
pause
```

В папке `Build\Result` появится файл `md2html.exe`.

## Пример использования (Windows)

1) Скопируйте папку `Пример` куда-нибудь
2) Выполните

```
:: Меняем кодировку консоли на UTF-8
chcp 65001

:: Указываем путь программе
set "PATH=c:\Programs\md2html"

:: Конвертируем *.md в *.html
md2html.exe Пример ПримерHtml

:: Ждём нажатия ENTER перед закрытием консоли
pause
```

В папку `ПримерHtml` будет помещен результат. Все md-файлы будут преобразованы в html.
Все не md-файлы будут просто скопированы в целевую папку.
В папке `ПримерHtml` будет создан файл `index.html`, а в папке `ПримерHtml\___res` будет создан файл `TagTable.js`.

3) Скопируйте папку `___res` из репозитория в `ПримерHtml`.


## Формулы

Формула внутри строки (inline): `` `$ формула $` `` или `` `\( формула \)` ``.<br>
Формула в центре отдельной строки: `` `$$ формула $$` `` или `` `\[ формула \]` ``.

Формулы набираются в формате LaTeX. Можно воспользоваться [онлайн-редактором](http://www.sciweavers.org/free-online-latex-equation-editor),
однако там есть далеко не все символы. Например:
* `\cdot` - dot protuct
* `\left|` и `\right|` - прямые скобки переменной высоты

Да одних пробелов существует целая куча:
* `\;` - толстый пробел
* `\:` - средний
* `\,` - тонкий
* `\!` - "отрицательный" пробел (то есть наложение)

Подробнее: <https://grammarware.net/text/syutkin/MathInLaTeX.pdf>.

## Теги

Теги должны находиться в конце документа в виде:

`**Теги: тег 1, тег 2**`

## Addon

Файл `___res/Addon.js` подключается последним и предназначен для пользовательского кода.
Dviglo имеет [свою версию этого файла](https://github.com/Dviglo/Dviglo/blob/master/Docs/Addon.js).

## Примечание

Для редактирования md-файлов удобно использовать Notepad++ с плагином Snippets.
