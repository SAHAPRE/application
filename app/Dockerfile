FROM python:3.9-slim

WORKDIR /app

# Now copy from the same context (the 'app' directory)
#COPY requirements.txt /app/requirements.txt
COPY . .

RUN pip install -r requirements.txt


CMD ["python", "app.py"]

