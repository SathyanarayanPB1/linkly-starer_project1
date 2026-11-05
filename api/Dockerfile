FROM python:3.12-slim-bookworm
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD [ "python" ,"healthcheck.py" ]
RUN useradd -u 10001 -d /app -m appuser
RUN chown -R appuser:appuser .
USER appuser 
CMD ["gunicorn", "app:app", "--bind", "0.0.0.0:5000"]