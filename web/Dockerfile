FROM python:3.7-slim

USER root
RUN python -m pip install --upgrade pip

WORKDIR pro

COPY . .


# COPY requirements.txt requirements.txt

RUN pip install -r requirements.txt

# RUN python manage.py makemigrations

# RUN python manage.py migrate

# RUN python manage.py collectstatic

RUN python tests/test.py

# RUN export $(cat .env | xargs) && python hello.py
CMD ["python","hello.py"]

EXPOSE 8000

