FROM python:3.12-slim-bookworm
WORKDIR /worker
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD [ "python" ,"healthcheck.py" ]
RUN useradd -u 10001   -d /worker/reports  -m appuser
RUN chown -R appuser:appuser /worker/reports
USER appuser
RUN ls -latr .
RUN ls -ld  .
CMD ["python","worker.py"]
# """Exit 0 if the worker wrote its heartbeat file in the last 30 seconds, else exit 1."""
