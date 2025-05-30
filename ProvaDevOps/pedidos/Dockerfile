FROM python:3.10
WORKDIR /app
COPY app.py .
RUN pip install flask redis mysql-connector-python requests
EXPOSE 3002
CMD ["python", "app.py"]
