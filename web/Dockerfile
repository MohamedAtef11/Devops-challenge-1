FROM python:3.7-slim

USER root
RUN python -m pip install --upgrade pip

WORKDIR pro

COPY . .

RUN pip install -r requirements.txt

RUN python tests/test.py

CMD ["python","hello.py"]

EXPOSE 8000

