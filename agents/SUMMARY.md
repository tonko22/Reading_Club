# Paper Notes

## Timeline

- **2016**: The first multi-agent framework was likely OpenAI's Gym, which allowed for the development and testing of reinforcement learning algorithms in a multi-agent environment.

- **March 20, 2023**: The paper ["Reflexion: Language Agents with Verbal Reinforcement Learning"](#reflexion-language-agents-with-verbal-reinforcement-learning) was published, introducing a novel framework for training language agents through linguistic feedback.

- **August 18, 2023**: Microsoft released AutoGen, an open-source framework designed for building AI agent systems. It facilitates the creation of scalable and resilient applications where AI agents can collaborate and perform tasks autonomously or with human oversight.

- **December 7, 2023**: The paper ["Practices for Governing Agentic AI Systems"](#practices-for-governing-agentic-ai-systems) was published, establishing foundational guidelines for the safe and responsible deployment of AI agents.

- **August 7, 2024**: The paper ["Scaling LLM Test Time Compute: Optimally Can Be More Effective Than Scaling Model Parameters"](#scaling-llm-test-time-compute-optimally-can-be-more-effective-than-scaling-model-parameters) was published, contributing to the discourse on optimizing large language models (LLMs) in multi-agent settings.

- **September 12, 2024**: OpenAI released O1-preview and O1-mini, a new series of AI models designed to spend more time thinking before responding. These models were specifically engineered for improved reasoning capabilities.

- **October 2, 2024**: A preview of AutoGen 0.4 was released, marking a significant update to the original AutoGen framework. This version focuses on enhancing the architecture and usability for developers working with agentic AI systems.

- **November 7, 2024**: The paper ["Magentic-One: A Generalist Multi-Agent System for Solving Complex Tasks"](#magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks) was published, presenting a new approach to multi-agent systems with improved planning and error recovery capabilities.

- **November 22, 2024**: The launch of CrewAI, a cutting-edge framework for managing AI agents, was announced. CrewAI enables the development of intelligent assistants and multi-agent teams, emphasizing collaborative intelligence.

## Papers

### Scaling LLM Test-Time Compute Optimally Can Be More Effective Than Scaling Model Parameters

**Authors**: Tianle Cai, Yuhao Wang, Zhengyang Geng, Jason D. Lee

**Link**: [Paper](papers/scaling-llm-test-time-compute-optimally-can-be-more-effective-than-scaling-model-parameters.pdf)

**Paper origin date**: 2024-08-07

### Summary

Идея: Можно улучшить производительность LLM на сложных задачах без увеличения размера модели за счет правильного управления вычислительными ресурсами во время инференса модели. 

- **Как это работает**:
  - Предсказываем количество подшагов, требуемых для решения задачи. Для этого используем отдельно обученую scoring-модель. 
  - Просим LLM декомпозировать задачу на соответствующее количество подшагов с помощью prompt-шаблона.
  - Решаем подшаги последовательными вызовами LLM, сверяясь с планом на каждом шагу.
  - Объединяем результаты подшагов в финальный ответ.
  - Опционально: Решаем задачу оптимизированного поиска по графу подшагов с помощью beam-search.

- **Ключевые находки**:
  - Маленькая модель с оптимизированным инференсом может показывать результаты на уровне больших моделей
  - Авторы разработали подход для декомпозиции задачи на подзадачи и определения оптимального момента остановки генерации
  - На практике это позволяет экономить до 40-50% вычислительных ресурсов без потери качества

- **Практические выводы**:
  - Не всегда нужно гнаться за увеличением количества параметров модели - часто можно получить тот же результат оптимизируя инференс
  - Важно правильно балансировать между длиной генерации и качеством результата
  - Для разных задач оптимальная стратегия может отличаться


## Practices for Governing Agentic AI Systems

**Authors**: Yonadav Shavit, Sandhini Agarwal, Miles Brundage, et al.

**Link**: [Paper](papers/practices-for-governing-agentic-ai-systems.pdf)

**Paper origin date**: 2023-12-07

### Summary

Идея: Создание базовых принципов и практик для безопасного внедрения агентных AI-систем в общество. Агентные системы - это AI-системы, способные преследовать сложные цели с ограниченным прямым контролем.

- **Как это работает**:
  - Определяются все участники жизненного цикла агентной системы
  - Для каждого участника формулируются базовые обязанности
  - Устанавливаются практики безопасности и контроля
  - Внедряются механизмы мониторинга и отчетности

- **Ключевые находки**:
  - Выделено 7 ключевых практик безопасности: оценка пригодности задачи, ограничение пространства действий, настройки поведения по умолчанию, прозрачность действий, автоматический мониторинг, атрибуция, возможность прерывания
  - Определены основные роли и ответственности в экосистеме агентных систем
  - Разработаны рекомендации по оценке и тестированию агентов

- **Практические выводы**:
  - Необходимо тщательно оценивать задачи перед передачей их агентным системам
  - Важно обеспечить многоуровневый контроль за действиями агентов
  - Следует уделять особое внимание редким ошибкам, которые могут накапливаться
  - Требуется баланс между автономностью агентов и безопасностью их работы

## Magentic-One: A Generalist Multi-Agent System for Solving Complex Tasks

**Authors**: Adam Fourney, Gagan Bansal, Hussein Mozannar, Cheng Tan, et al.

**Link**: [Paper](papers/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks.html)

**Paper origin date**: 2024-11-07

### Summary

Идея: Создание универсальной мультиагентной системы, способной решать сложные задачи за счет эффективного планирования, многошагового рассуждения и восстановления после ошибок.

- **Как это работает**:
  - Главный агент "Orchestrator" управляет процессом:
    - Создает и отслеживает план выполнения
    - Перепланирует при возникновении ошибок
    - Координирует специализированных агентов
  - Специализированные агенты выполняют конкретные задачи (веб-браузинг, работа с файлами, программирование)
  - При ошибках система автоматически адаптирует стратегию

- **Ключевые находки**:
  - Модульная архитектура позволяет легко добавлять и удалять агентов
  - Не требуется дополнительная настройка промптов при изменении команды агентов
  - Система показывает результаты на уровне state-of-the-art на нескольких бенчмарках
  - Подтверждена эффективность мультиагентного подхода для универсальных систем

- **Практические выводы**:
  - Мультиагентный подход эффективнее одиночных агентов для сложных задач
  - Важно обеспечить правильную координацию между агентами
  - Модульность и гибкость архитектуры упрощают развитие системы
  - Открытый исходный код позволяет использовать наработки в других проектах

## Timeline

- **2016**: The first multi-agent framework was likely OpenAI's Gym, which allowed for the development and testing of reinforcement learning algorithms in a multi-agent environment.

- **August 18, 2023**: Microsoft released AutoGen, an open-source framework designed for building AI agent systems. It facilitates the creation of scalable and resilient applications where AI agents can collaborate and perform tasks autonomously or with human oversight.

- **August 7, 2024**: The paper "Scaling LLM Test Time Compute: Optimally Can Be More Effective Than Scaling Model Parameters" was published, contributing to the discourse on optimizing large language models (LLMs) in multi-agent settings.

- **September 12, 2024**: OpenAI released O1-preview and O1-mini, a new series of AI models designed to spend more time thinking before responding. These models were specifically engineered for improved reasoning capabilities.

- **October 2, 2024**: A preview of AutoGen 0.4 was released, marking a significant update to the original AutoGen framework. This version focuses on enhancing the architecture and usability for developers working with agentic AI systems.

- **November 22, 2024**: The launch of CrewAI, a cutting-edge framework for managing AI agents, was announced. CrewAI enables the development of intelligent assistants and multi-agent teams, emphasizing collaborative intelligence.
