# AI Framework Examples

Этот репозиторий содержит примеры использования фреймворка из ai-framework-core

## Быстрый старт

Перед использованием примеров необходимо установить основные зависимости

### 1. Установка базового фреймворка
```bash
# Перейдите в репозиторий с ядром фреймворка
cd ../ai-framework-core

# Установите пакет в режиме разработки
pip install -e .
```

### 2. Установка зависимостей для примеров
```bash
# Вернитесь в папку с примерами
cd ../ai-framework-examples

# Установите дополнительные зависимости для примеров
pip install -r requirements.txt
```

## Структура примеров

### basic_usage/
Базовые примеры использования фреймворка
- `simple_chain.py` - Простая цепочка с FakeLLM
- `async_agent.py` - Асинхронный агент с инструментами
- `patterns_demo.py` - Примеры использования паттернов

### advanced_patterns/
Продвинутые сценарии и архитектурные паттерны
- `factory_pattern.py` - Использование фабрик для создания компонентов
- `observer_demo.py` - Паттерн Наблюдатель в цепочках
- `decorator_examples.py` - Декораторы для кеширования и повторов

### async_demos/
Асинхронные примеры и работа с множеством агентов
- `parallel_agents.py` - Параллельное выполнение нескольких агентов
- `async_tools.py` - Асинхронные инструменты
- `performance_test.py` - Тесты производительности

### docker_demos/
Примеры для Docker-развертывания
- `local_test.py` - Тестирование перед развертывания
- `api_client.py` - Клиент для веб-API
- `integration_test.py` - Интеграционные тесты

### tests/
Интеграционные тесты и проверки
- `test_basic_functionality.py` - Тесты базовой функциональности
- `test_async_operations.py` - Тесты асинхронных операций
- `test_integration.py` - Интеграционные тесты с сервисами

## Требования

Основные зависимости уже установлены с ai-framework-core
Дополнительные зависимости для примеров:

```txt
# Тестирование
pytest>=7.0.0
pytest-asyncio>=0.21.0

# Jupyter ноутбуки (опционально)
jupyter>=1.0.0
ipykernel>=6.0.0

# Визуализация (для расширенных примеров)
matplotlib>=3.5.0  # Для графиков производительности
networkx>=2.8.0    # Для визуализации цепочек
```

## Как использовать примеры

### Запуск базового примера
```bash
python basic_usage/simple_chain.py
```

### Запуск асинхронного примера
```bash
python async_demos/parallel_agents.py
```

### Запуск тестов
```bash
pytest tests/ -v
```

### Запуск в режиме разработки
```bash
# С автоматической перезагрузкой при изменениях
pip install watchdog
python -m watchdog observe basic_usage/ --recursive --command='python basic_usage/simple_chain.py'
```

## Настройка окружения

### Для разработки с использованием workspace VSCode
Рекомендуется открыть весь проект через workspace файл:
```bash
# Откройте ai-framework.code-workspace в VSCode
code ai-framework.code-workspace
```

### Прямой запуск без workspace
```bash
# Убедитесь, что Python может найти модули ядра
export PYTHONPATH="${PYTHONPATH}:../ai-framework-core/src"

# Запустите пример
python basic_usage/simple_chain.py
```

## Поиск и устранение неисправностей

### Ошибка импорта модулей
Если возникает ошибка "ModuleNotFoundError: No module named 'ai_framework'":
```bash
# Убедитесь, что вы установили ai-framework-core
cd ../ai-framework-core && pip install -e . && cd ../ai-framework-examples
```

### Проблемы с асинхронностью
Для асинхронных примеров используйте:
```bash
python -m async_demos.parallel_agents
```

### Проблемы с путями
Добавьте путь к ядру вручную:
```python
import sys
import os
sys.path.append(os.path.join(os.path.dirname(__file__), '..', 'ai-framework-core', 'src'))
```

## Создание собственных примеров

Шаблон для нового примера:
```python
"""
Пример использования [название компонента]
"""

import asyncio
import sys
import os

# Добавление пути к ядру фреймворка
sys.path.append(os.path.join(os.path.dirname(__file__), '..', 'ai-framework-core', 'src'))

from llms import FakeLLM
from chains import SimpleLLMChain

async def main():
    """
    Основная функция примера
    """
    # Создание компонентов
    llm = FakeLLM(response="Это тестовый ответ")
    chain = SimpleLLMChain(llm=llm, prompt_template="Вопрос: {input}")
    
    # Использование цепочки
    result = await chain.run({"input": "Привет, мир!"})
    print(f"Результат: {result}")

if __name__ == "__main__":
    asyncio.run(main())
```

## Вклад в проект

Для добавления новых примеров:

1. Создайте файл в соответствующей категории
2. Добавьте понятные комментарии
3. Убедитесь, что пример работает
4. Обновите этот README.md при необходимости

## Лицензия

Этот проект лицензирован под MIT License - смотрите файл LICENSE для деталей

## Получение помощи

Если у вас возникли проблемы с примерами:

1. Проверьте, что ai-framework-core установлен правильно
2. Убедитесь, что все зависимости установлены
3. Проверьте пути импорта в примерах
4. Создайте issue в основном репозитории ai-framework-core

Удачного использования фреймворка!