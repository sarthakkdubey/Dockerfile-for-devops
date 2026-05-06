
#==========Base Image==========

#using this as base layer and using slim----lightweight
FROM python:3.12-slim

#Prevent Python from writing .pyc files
ENV PYTHONDONTWRITEBYTECODE=1

#Prevent Python output buffering
ENV PYTHONUNBUFFERED=1

#set working directory
WORKDIR /app

#Copy dependency file
COPY requirements.txt .

#install dependencies from source to container
RUN pip install --no-cache-dir -r requirements.txt

#Copy application files from source to our container
COPY . .

#Expose application port 
EXPOSE 8000

#run application--using cmd so can be rewritten
CMD ["python", "app.py"]
