FROM python:3.13

# Set working directory
WORKDIR /app

# Bring the system up to date
RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*

# Install poetry
ENV POETRY_HOME=/opt/poetry
ENV PATH="${POETRY_HOME}/bin:$PATH"
RUN curl -sSL https://install.python-poetry.org | python -

# Copy toml and lock
COPY pyproject.toml .
COPY poetry.lock .

# Install project dependencies
RUN poetry install --no-root

# Copy the rest of the application code
COPY . ./app/

# Expose port for FastAPI
ENV PORT=83

# Start the FastAPI application
# CMD ["poetry", "run", "uvicorn", "app.main:app", "--host 0.0.0.0", "--port", $PORT, "--reload"]
CMD exec poetry run uvicorn app.main:app --host 0.0.0.0 --port $PORT --reload
