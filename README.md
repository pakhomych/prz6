# 2. Фаззинг-тестирование приложения

## Исходный код

Выберем цель для нашего теста, а так же набор входных данных:
- `git clone https://github.com/eduardoParedes/Text-File-Reader.git`
- `git clone https://github.com/openpreserve/format-corpus.git`

### Makefile

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
