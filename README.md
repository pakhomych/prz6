# 2. Фаззинг-тестирование приложения

## Исходный код

В качестве тестового проекта используем: https://github.com/eduardoParedes/Text-File-Reader

- Загрузим проект

    git clone https://github.com/eduardoParedes/Text-File-Reader.git

- Сборка
```Makefile
    CC = gcc

    TARGET = words 
    SOURCES = words.c
    OBJECTS = $(SOURCES:.c=.o)

    all: $(TARGET)

    $(TARGET): $(OBJECTS)
	    $(CC) $(OBJECTS) -o $(TARGET)

    %.o: %.c
	    $(CC) $(CFLAGS) -c $< -o $@

    clean:
	    rm -f $(OBJECTS) $(TARGET) *.gcda *.gcno core *~
```
