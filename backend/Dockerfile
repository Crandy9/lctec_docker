# build stage (for caching dependencies)
FROM python:3.13-slim AS build

WORKDIR /backend

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
       libpq-dev gcc build-essential python3-dev \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .

# Install dependencies in build stage to leverage caching
RUN pip install --upgrade pip \
    && pip install --no-cache-dir -r requirements.txt

COPY . .

# runtime stage
FROM python:3.13-slim

WORKDIR /backend

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    PATH="/usr/local/bin:$PATH" 

# Install minimal runtime dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
       libpq-dev \
    && rm -rf /var/lib/apt/lists/*    

# Copy the backend code and copy pip-installed executables like celery
COPY --chown=lctec:lctec --from=build /backend /backend
COPY --from=build /usr/local /usr/local

# Create user and switch
RUN useradd -m lctec
USER lctec

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "Main_Project.wsgi:application"]