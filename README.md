# MLOps HW1 ШАД (ML Inference service)

## Описание

Этот сервис выполняет автоматический inference модели CatBoost на данных первого соревнования

- следит за появлением новых файлов `test.csv` в папке `/input`
- применяет к ним предобработку (как в соревновании)
- делает предсказания с использованием уже готовой модели (из соревнования) 
- сохраняет результат в виде csv файла в `/output`


Команды: 

1. docker build -t ml-inference-service .
2. docker run -it --rm -v ./input:/app/input \
                    -v ./output:/app/output \
                    ml-inference-service


Архитектура: 

├── .gitignore
├── Dockerfile
├── README.md
├── app/
│ └── app.py # Ядро сервиса с обработчиком файлов
├── model/
│ └── my_catboost.cbm # Сериализованная модель CatBoost
├── src/
│ ├── preprocessing.py # Пайплайн обработки данных
│ └── scorer.py # Модуль прогнозирования
└── input/ # Директория для загрузки файлов на скоринг
    └── test.csv 
└── output/ # Директория с результатами скоринга