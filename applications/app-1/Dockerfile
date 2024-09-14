FROM python:3.12-slim AS builder
WORKDIR /app
RUN apt-get update && apt-get install -y --no-install-recommends \
    make \
    zip \
    && rm -rf /var/lib/apt/lists/*

RUN python -m pip install --no-cache-dir poetry
COPY pyproject.toml poetry.toml /app/
RUN poetry install --no-dev --no-interaction --no-ansi

COPY . /app/
RUN make dist-clean clean build ssap package

FROM python:3.12-slim AS final
WORKDIR /app
RUN apt-get update && apt-get install -y --no-install-recommends unzip && rm -rf /var/lib/apt/lists/*

COPY --from=builder /app/.venv /app/.venv
ENV PATH="/app/.venv/bin:${PATH}"

COPY --from=builder /app/dist/package/applications.zip /app/
RUN unzip applications.zip && rm applications.zip

EXPOSE 8501
CMD ["streamlit", "run", "app_1/handler.py"]


