# Лабораторная работа №1 (Сегментация и аннотация текста)

## Синопсис лекции

**Токенизация** - разбиение текста на осмысленные элементы (слова, фразы, символы), называемые *токенами*.

Примеры простой токенизации на языке программирования `python` с использованием регулярных выражений:

```py
re.split(r' ', raw) 
re.split(r'[ \t\n]+', raw) 
re.split(r'\W+', raw)
```

**Стемминг** - это процесс нахождения основы слова для заданного исходного слова. Основа слова не обязательно совпадает с морфологическим корнем слова.

**Лемматизация** - процесс приведения словоформы к лемме — её нормальной (словарной) форме.

## Задание

1. Необходимо разработать токенизатор на основе регулярных выражений. При токенизации должен корректно обрабатываться текст выбранного датасета (см. [указания к выполнению лабораторных работ](../README.md));

2. Необходимо выполнить стемминг, используя одну из существующих библиотек, например, `nltk` для языка программирования `python` (см. `SnowballStemmer`);

3. Необходимо выполнить лемматизацию, используя одну из существующих библиотек, например `nltk` для языка программирования `python` (см. `WordNetLemmatizer`);

4. Проверить результаты лемматизации. Для лемматизации и проверки можно использовать дополнительные датасеты. В отчете привести примеры случаев омонимии (порождено несколько гипотез для одной словоформы), объяснить полученные результаты;

5. Сформировать для текста выбранного датасета аннотацию в формате `tsv` в соответствии со следующей структурой:
```tsv
<sentence_1_token_1>	<sentence_1_stem_1> <sentence_1_lemma_1>
<sentence_1_token_2>	<sentence_1_stem_2>	<sentence_1_lemma_2>
...
<sentence_1_token_N>	<sentence_1_stem_N>	<sentence_1_lemma_N>

<sentence_2_token_1>	<sentence_2_stem_1>	<sentence_2_lemma_1>
<sentence_2_token_2>	<sentence_2_stem_2>	<sentence_2_lemma_2>
...
<sentence_2_token_N>	<sentence_2_stem_N>	<sentence_2_lemma_N>
```

Пример фрагмента результирующего файла:
```tsv
Клиника	клиник	клиника	
располагается	располага	располагаться
в	в	в	
центре	центр	центр	
столицы	столиц	столица
```

Результаты выполнения работы необходимо разместить в директории `/projects/<PROJECT_NAME>/assets/annotated-corpus` (путь указан относительно корня репозитория, `<PROJECT_NAME>` следует заменить на название проекта). В данной директории необходимо сформировать каталоги `train` и `test`, в которых будет размещаться набор файлов с расширением `tsv`, содержащие аннотации документов, составляющих исходный датасет. Каждому документу исходного датасета соответствует отдельный файл, в качестве названия файла используется идентификатор документа (если документам в исходном датасете уже присвоены некоторые идентификаторы, необходимо использовать их, если идентификаторы отсутствуют - необходимо их сформировать самостоятельно). Документы группируются по директориям в соответствии с их разбиением на классы, название класса используется в качестве названия соответствующей директории.  

Например, если исходный датасет (train) имеет следующий вид:
```csv
"doc_id","label","text"
"001","cat","Meow meow 😺😺"
"002","dog","Woof woof 🐕🐕"
```

То структура каталога `/projects/<PROJECT_NAME>/assets/annotated-corpus/train` должна выглядеть следующим образом:
```sh
.
├── cat
│   └── 001.tsv
└── dog
    └── 002.tsv

2 directories, 2 files
```
