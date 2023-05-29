# 2. Фаззинг-тестирование приложения

## Исходный код

Выберем цель для нашего теста, а так же корпус входных данных:
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

clean:
	rm -f $(OBJECTS) $(TARGET) *.gcda *.gcno core *~
```

## Сборка и тест проекта с санитайзерами

`cmake . -D CMAKE_C_COMPILER=afl-cc -D CMAKE_CXX_COMPILER=afl-c++`

`AFL_USE_ASAN=1 AFL_USE_UBSAN=1 make -j20`

`find ./input -type f -exec ./words {} \;`

## Результат теста

!(./img/san-test.png)
