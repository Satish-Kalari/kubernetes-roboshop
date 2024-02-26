FROM python:3.9.18-alpine3.19

EXPOSE 8080
# Following variable user anme and passowrd is for payment to intract with rabbitmq
ENV AMQP_USER=roboshop \
    AMQP_PASS=roboshop123
USER root # change the user to root
WORKDIR /app
COPY requirements.txt /app/
RUN pip install -r requirements.txt
COPY *.py /app/
COPY payment.ini /app/
#CMD ["python", "payment.py"]
CMD ["uwsgi", "--ini", "payment.ini"]